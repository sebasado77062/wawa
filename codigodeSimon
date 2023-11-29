//pines de las conexiones
int entrada1 = 8; //boton amarillo
  int entrada2 = 9; //boton azul
  int entrada3 = 10; //boton verde
  int entrada4 = 11; //boton rojo

int salida1 = 2; //led amarillo
  int salida2 = 3; //led azul
  int salida3 = 4; //led verde
  int salida4 = 5; //led rojo

int buzzer = 6; //zumbador

//pines del rgb ---> necesita mas desarrollo si es que se lo va a dejar
  int rojo = 13;
  int verde = 7;
  int azul = 12;

//variables para variar de lo programacionistico
	int nivel = 1;
	int const nivelm = 100;  // nivel maximo 
	int velocidad = 500;
	int secuenciam[nivelm]; //secuencia hecha por la maquinaria toda re polenta
    int secuenciau[nivelm]; //secuencia hecha por el usuario (igual que la cantidad de niveles para que el usuario los pueda jugar todos)


//funciones de las secuencias
void inicio(){  
 for (int i = 1; i <= 6; i++) {
   digitalWrite(salida4 , HIGH);
   	tone(buzzer, 400);
   delay(100);
   	noTone(buzzer);
   digitalWrite(salida4 , LOW);
   digitalWrite(salida1 , HIGH);
   	tone(buzzer, 100);
   delay(100);
   	noTone(buzzer);
   digitalWrite(salida1, LOW);
   digitalWrite(salida2 , HIGH);
   	tone(buzzer, 200);
   delay(100);
   	noTone(buzzer);
   digitalWrite(salida2, LOW);
   digitalWrite(salida3 , HIGH);
   	tone(buzzer, 300);
   delay(100);
   	noTone(buzzer);
   digitalWrite(salida3 , LOW);
 } 
}

void generarsecuencia(){
	randomSeed(analogRead(A5));
  	for(int i = 0; i < nivelm; i++){
      secuenciam[i] = random(2,6); //se asignara un numero aleatorio (entre el 2 y el 5 (el 6 no lo incluye porque empiea a contar desde el cero el arduino)) a cada posicion dentro del vector secuenciam para que asi coincida con los pines de los leds y estos se enciendan 
    }
}

void mostrarsecuencia(){ //aparte de mostrarla va a emitir un sonido re fachero (cada led o color un sonidito diferente)
	digitalWrite(salida1, LOW);
  	digitalWrite(salida2, LOW);
  	digitalWrite(salida3, LOW);
  	digitalWrite(salida4, LOW);
  for(int i = 0; i < nivel; i++){
    if(secuenciam[i] == salida1){
      tone(buzzer, 100);
      delay(250);
      noTone(buzzer);
    }
    if(secuenciam[i] == salida2){
      tone(buzzer, 200);
      delay(250);
      noTone(buzzer);
    }
    if(secuenciam[i] == salida3){
      tone(buzzer, 300);
      delay(250);
      noTone(buzzer);
    }
    if(secuenciam[i] == salida4){
      tone(buzzer, 400);
      delay(250);
      noTone(buzzer);
    }
    //esto se puede sacar si es que 
    //solo queremos que el led rgb muestre la secuencia
    //(en caso de que se quarramos agregarle más dificultad)
  digitalWrite(secuenciam[i], HIGH);
  delay(velocidad);
  digitalWrite(secuenciam[i], LOW);
  delay(250);
  
  }
}

void comprobarsecuencia(){ 
int entradavalida = 0;
   for(int i = 0; i < nivel; i++){
      entradavalida = 0;
      while(entradavalida == 0){
         if(digitalRead(entrada4) == HIGH){
            digitalWrite(salida4, HIGH);
            tone(buzzer, 400);
            delay(300);
            noTone(buzzer);
            secuenciau[i] = salida4;
            delay(200);
            if(secuenciau[i] != secuenciam[i]){
               secuenciaError();
               return;
            }
            entradavalida = 1;
            
            digitalWrite(salida4, LOW);
         }
         if(digitalRead(entrada3) == HIGH){
            digitalWrite(salida3, HIGH);
            tone(buzzer, 300);
            delay(300);
            noTone(buzzer);
            secuenciau[i] = salida3;
            delay(200);
            if(secuenciau[i] != secuenciam[i]){
               secuenciaError();
               return;
            }
            entradavalida = 1;
            
            digitalWrite(salida3, LOW);
         }
         if(digitalRead(entrada2) == HIGH){
            digitalWrite(salida2, HIGH);
            tone(buzzer, 200);
            delay(300);
            noTone(buzzer);
            secuenciau[i] = salida2;
            delay(200);
            if(secuenciau[i] != secuenciam[i]){
               secuenciaError();
               return;
            }
            entradavalida = 1;
            
            digitalWrite(salida2, LOW);
         }
         if(digitalRead(entrada1) == HIGH){
            digitalWrite(salida1, HIGH);
            tone(buzzer, 100);
            delay(300);
            noTone(buzzer);
            secuenciau[i] = salida1;
            delay(200);
            if(secuenciau[i] != secuenciam[i]){
               secuenciaError();
               return;
            }
            entradavalida = 1;
            
            digitalWrite(salida1, LOW);
         }
      }
   }
   secuenciaCorrecta();
}

void secuenciaError(){
  for(int i = 0; i < 3; i++){
   digitalWrite(salida1, HIGH);
   digitalWrite(salida2, HIGH);
   digitalWrite(salida3, HIGH);
   digitalWrite(salida4, HIGH);
   tone(buzzer, 1000);
   delay(250);
   digitalWrite(salida1, LOW);
   digitalWrite(salida2, LOW);
   digitalWrite(salida3, LOW);
   digitalWrite(salida4, LOW);
   noTone(buzzer);
   delay(250);
  }
   nivel = 1;
   velocidad = 500;
   return;

}


void secuenciaCorrecta(){
  if(nivel < nivelm){
    nivel = nivel + 1;
   velocidad -= 3;
    delay(200);
   tone(buzzer, 600);
    delay(200);
   noTone(buzzer);
   tone(buzzer, 700);
    delay(200);
   noTone(buzzer);
    delay(500);
  }
}

void setup()
{
	pinMode(entrada1, INPUT);
    pinMode(entrada2, INPUT);
  	pinMode(entrada3, INPUT);
  	pinMode(entrada4, INPUT);
  
  	pinMode(salida1, OUTPUT);
  	pinMode(salida2, OUTPUT);
  	pinMode(salida3, OUTPUT);
  	pinMode(salida4, OUTPUT);

	pinMode(buzzer, OUTPUT);
}
	//si el generarsecuencia(); se coloca aquí 
    //en lugar del void loop(), entonces será la misma 
    //secuencia siempre

void loop() 
{

     if(nivel == 1){
       //si el generarsecuencia(); se coloca aquí
       //en lugar de void setup(), entonces se generará
       //una secuencia diferente cada vez que se
       //se vuelva al nivel 1
       generarsecuencia(); 
       delay(100);
       inicio();
       delay(200);
       mostrarsecuencia();
      comprobarsecuencia();
   } else {
      mostrarsecuencia();
      comprobarsecuencia();
   }
}
