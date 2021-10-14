#include “LiquidCrystal_I2C.h”

#include “DHT.h”

#define DHTPIN 8

#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

LiquidCrystal_I2C lcd(0x27, 16, 2);

int sensor_Pin = A0;

double sensor_Value = 0;

double moisture_Value = 0;

const int MOISTURE_LEVEL = 300;

void setup() {

Serial.begin(9600);

dht.begin();

lcd.begin();

pinMode(7, OUTPUT);

pinMode(12, OUTPUT);

pinMode(13, OUTPUT);

}

void loop() {

float t = dht.readTemperature(true);

sensor_Value = analogRead(sensor_Pin);

Serial.print(“Soil Moisture Sensor Value = “);

Serial.print(sensor_Value);

moisture_Value = (sensor_Value * 100) / 1000;

moisture_Value = 100 – moisture_Value;

Serial.print(” Soil Moisture Value = “);

Serial.print(moisture_Value);

Serial.println(” %”);

Serial.print(” Temp = “);

Serial.print(t);

Serial.println(” C”);

lcd.setCursor(0, 0);

lcd.print(“Temp=” + String(t) + ‘C’);

lcd.setCursor(0, 1);

lcd.print(“Moisture=” + String(moisture_Value) + ‘%’);

if(sensor_Value > MOISTURE_LEVEL){

digitalWrite(7,HIGH);

digitalWrite(13,HIGH);

digitalWrite(12,LOW);

}

else {

digitalWrite(7,LOW);

digitalWrite(13,LOW);

digitalWrite(12,HIGH);

}

delay(1000);

}
