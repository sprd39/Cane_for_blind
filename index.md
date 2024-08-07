# Walking Stick For the Visually Impaired 
My project is a Smart Walking Stick for the Visually Impaired. It helps the visually people cross streets, navigate potential obstacles, and helps them go about their day! It has a ultrasonic sensor that detects objects and plays a higher sound the closer the object is. I also have a water sensor attached to detect puddles. However, none of this could be possible without me joining Bluestamp. I joined Bluestamp to bridge the gap between my software engineering background and the tangible world of hardware. Working with an Arduino, connecting wires, experimenting with resistors, and integrating various sensors was a thrilling new challenge that pushed me to expand my engineering skill set.


You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Saanvi P. | The Bishop's School |  Engineering | Incoming Freshman

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

<!--- **Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.** -->

<!--- <iframe width="560" height="315" src="https://youtu.be/EWFnbWfkoFg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> -->

Since my previous milestone, I actually put all my wires and sensors together in a usable product that people can use. I placed the Arduino, breadboard, speaker, and vibrating module in the box; the ultrasonic and water sensors were outside of the box. Now, this cane can be used by a user. This wouldn't have been possible through everything I learned at BSE. I learned how to use an Arduino, attach different wires into the breadboard, how different sensors work, and how to code using the Arduino language. This was a hands-on approach I had never experienced while engineering. In the future, I hope to take all the knowledge I learned at BSE to improve my current project by adding more sensors and creating new projects.



# Second Milestone 

<!--- **Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.** -->

 <iframe width="560" height="315" src="https://youtu.be/zkXQQrSQfwMhttps://youtu.be/zkXQQrSQfwM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

I have worked on many things for this milestone. I added a sound that changes based on how far the object is. For example, if an object is detected less than 14cm away a different sound will play than a object detected 27cm away. Another thing I added for this milestone was my water sensor to help detect puddles. It will print on the serial moniter on the computer of how deep the water is. For my next steps I plan to add actual serial moniter (not just my computer) and attach it to my walking stick. If I have enough time, I will try to add a temparature sensor. One challenge that I faced was using my water sensor. The readings were the exact opposite of what I wanted them to be. When it was out of the water, the readings were supposed to be low and high inside the water. However, it was the exact opposite for me. I solved this by changing the code to fit this. When the sensor read a low number, I coded it so that the serial moniter would print that something was in the water. 

# First Milestone



<iframe width="560" height="315" src="https://www.youtube.com/embed/agOPqsIDC58?si=H66SDbOYAmRz9fC6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

I have completed my first milestone! I have finished the wiring of the different components such as the arduino, ultrasonic sensor, and the vibrating motor. This code continuously measures the distance using an ultrasonic sensor. If an object is detected within a certain range, the code activates the motor and sounds the buzzer as an alarm. The delay between measurements prevents overwhelming the sensor and allows for smoother operation. Next, I plan to find a way to store all of this wiring into a box, so that it can be attached to the walking cane. I also plan to add a speech when an object is a certain distance away, not just a loud buzzing noise. 


# Schematics 
#Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
#Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
#define trigPin 11
#define echoPin 12
#define motor 7
#define buzzer 3
#define switchPin 5

const int read = A1; //Sensor AO pin to Arduino pin A0
int value;   

long duration, cm;

#include"pitches.h"

void setup() {
 Serial.begin(9600);
 pinMode(trigPin, OUTPUT);
 pinMode(echoPin, INPUT);
 pinMode(motor, OUTPUT);
 pinMode(buzzer, OUTPUT);
 pinMode(switchPin, OUTPUT);
 pinMode(read,INPUT);
}

void loop() {
 // Calculate distance
 digitalWrite(trigPin, LOW);
 delayMicroseconds(2);
 digitalWrite(trigPin, HIGH);
 delayMicroseconds(10);
 digitalWrite(trigPin, LOW);
 duration = pulseIn(echoPin, HIGH);
 cm = microsecondsToCentimeters(duration);

if(cm <= 14 )
 {
   tone(switchPin, 784);
   digitalWrite(switchPin, HIGH);
   delay(1000);
   Serial.println("in condition 1");
    digitalWrite(motor,HIGH); // When the the distance below 100cm
    digitalWrite(buzzer,HIGH);
 }
   else if(cm <= 24)
   {
      tone(switchPin, 698);
      delay(1000);
      Serial.println("in condition 2");
       digitalWrite(motor,HIGH); // When the the distance below 100cm
       digitalWrite(buzzer,HIGH);
   }
   else if(cm <= 34 )
   {
     tone(switchPin, 659);
     delay(1000);
     Serial.println("in condition 3");
      digitalWrite(motor,HIGH); // When the the distance below 100cm
      digitalWrite(buzzer,HIGH);
   }
   else if(cm <= 44)
   {
     tone(switchPin, 587);
     delay(1000);
     Serial.println("in condition 4");
      digitalWrite(motor,HIGH); // When the the distance below 100cm
      digitalWrite(buzzer,HIGH);
   }
   else if(cm <= 55 )
   {
     tone(switchPin, 523);
     delay(1000);
     Serial.println("in condition 5");
      digitalWrite(motor,HIGH); // When the the distance below 100cm
      digitalWrite(buzzer,HIGH);
   }
   else if(cm <= 65 )
   {
     tone(switchPin, 494);
     delay(1000);
     Serial.println("in condition 6");
      digitalWrite(motor,HIGH); // When the the distance below 100cm
     digitalWrite(buzzer,HIGH);
   }
 else
 {
   noTone(switchPin);
   digitalWrite(switchPin, LOW);
 }
 delay(100);
value = analogRead(read);
Serial.println(value);
  if (value >=540){
   Serial.println("Water level: 0mm - Empty!");
 }
 else if (value>220 && value<=260){
   Serial.println("Water level: 0mm to 5mm");
 }
 else if (value>185 && value<=220){
   Serial.println("Water level: 5mm to 10mm");
 }
 else if (value>177 && value<=185){
   Serial.println("Water level: 10mm to 15mm");
 }
 else if (value>172 && value<=176){
   Serial.println("Water level: 15mm to 20mm");
 }
 else if (value>168 && value<=171){
   Serial.println("Water level: 20mm to 25mm");
 }


}


long microsecondsToCentimeters(long microseconds) {
 return microseconds / 29 / 2;
}
```

# Bill of Materials


| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| ELEGOO UNO Project Super Starter Kit | Wiring,Arduino | $44.99 | <a href="https://www.amazon.com/ELEGOO-Project-Tutorial-Controller-Projects/dp/B01D8KOZF4/ref=sr_1_3_pp?crid=2CDRMQVSYOD4H&dib=eyJ2IjoiMSJ9.AcWZy-Yg4mDTnhzEHozxzPZdVC5-KUL2tW-OQewDKpA7ZhEVnlvYJFELmn1cEN5uvrZVxp4St_nlIhbtJibvxUj7s5mZJHZ5gTUoGHyjSCEJnV1m-a2PWxrXyWYqZrufz70WGPo3NV3-f7iFEXccDbUvJu8BRvjxPCjgkJ_uJnDxpPk3Gjw_yw7XMWWb8ll4GsOLKWrxeEr1uOS5BeD0EU2Y1MvZXAOcITMnykL7K69Fr4P6SnWB2EpkaJ37raPdYGD096Z_rSPyEsRfxIx6Rv9N65w4nRID980vI94aLYQ.PuIIln1now7ULLLgzCb0zPl5SBpDXd-IT05ToFwhflM&dib_tag=se&keywords=arduino+starter+kit&qid=1720652047&s=industrial&sprefix=arduino+starter+ki%2Cindustrial%2C72&sr=1-3"> Link </a> |
| 8-Count 9 Volt Alkaline Performance All-Purpose Batteries | Power | $12.36 | <a href="https://www.amazon.com/Amazon-Basics-Performance-All-Purpose-Batteries/dp/B00MH4QM1S/ref=sr_1_5_pp?crid=3TQ7ANPH958JM&dib=eyJ2IjoiMSJ9.bmcV2Upj_vpB6G9CFlPPxYAryat512da7ekZjc52HecXSTmtx7PbJ50EgQFPCMqlAxjOUq-tL4vQTpozlHvH89bMwx-HJoyGcdz6EY8HrMxahTiqOXkoP7ewkDcgHoMhmHamdlQfW6FBHO0Gm-DYZZnnMuvEU3qOpemA8PGEvRhEx4-lGaBZhrvls039G1-9SizAW-YRGXZ2fFrdVDlREyyOhAuxXZaE5QqUxWesRQgP9UfGOYaInRWTTPwhDbXFa-RPzGbU1C_u4wq-NMqKBtWEQqR9-cA8O3FYOx3icEY.dtKJmI2T-iCmMM_bYnbiHUWzhKpJDRxS-bBmZIwYFKM&dib_tag=se&keywords=9v+batteries&qid=1720651326&rdc=1&s=electronics&sprefix=9v+batteries%2Celectronics%2C105&sr=1-5"> Link </a> |
| Walking Cane | Base for project | $10.99 | <a href="https://www.amazon.com/dp/B0CDMD98WW?ref=cm_sw_r_cso_cp_apin_dp_K5GQXJSBZVNS5YNW3NEM&ref_=cm_sw_r_cso_cp_apin_dp_K5GQXJSBZVNS5YNW3NEM&social_share=cm_sw_r_cso_cp_apin_dp_K5GQXJSBZVNS5YNW3NEM&starsLeft=1&th=1"> Link </a> |
| Vibrating Motor Module | To alert user | $8.69 | <a href="https://www.amazon.com/DAOKI-Vibration-Vibrating-Vibrator-Electronic/dp/B081W4CTNY/ref=sr_1_4?crid=1HIXGEJDEQ1Z8&dib=eyJ2IjoiMSJ9.UIpViK-oNwsFrMDYjG2mw3JjFsvLvCct4jBnGPCSo3LQMbiJOKjyeuWRfkNfwhST0U5WEHAzNvZLIjx7uXHiS4fmxQmtaA4o7lv7RuXwsmYeqLFknXDEMmpu-UKXYitCdIfaJy6Lt0sfe_oKM3FnhBjvyvO6pogMdftUXUMXymAmnhrENGlaP2DgzmtsTk62Rly2EDGGEqdpSCimbQzwHs_We_eMeC9bWOlNvvns2qBTbAdV78gG7NzbSd_6bDqhNhF7jZPQ6QKz6pDM6ozSWfFNYhgdfEBcfCTJ8n7hmG0.31LckcCEIL5OgrFyW2AhGX13FpyOuD8HN9kjfFZ103Y&dib_tag=se&keywords=vibrating+motor+arduino&qid=1720652605&s=industrial&sprefix=vibrating+motor+arduino%2Cindustrial%2C75&sr=1-4"> Link </a> |
| Wire Screw Terminal Block Connector | Connecting thin wires | $11.99 | <a href="https://www.amazon.com/SimpoÂ®-24-12AWG-Breadboard-Terminal-Connector/dp/B07DG3GM42/ref=sr_1_2?crid=8JKOUOXW1A8L&dib=eyJ2IjoiMSJ9.zk1RfO7WeUH5yeN54oOKyogK-ABZhwrqV5eLv6cALK52iBfiZoXVZtqgdUHtvdu00V8sQ9HP4BYMBVBYTwDefbO1DhcMO71NauPTuLFI&th=1"> Link </a> |
| Rain Drops Sensor | Sensing Puddles | $6.49 | <a href="https://www.amazon.com/HiLetgo-Moisture-Humidity-Sensitivity-Nickeled/dp/B01DK29K28/ref=sr_1_fkmr0_2?crid=2L4A45ZA4B44Q&dib=eyJ2IjoiMSJ9.wNagNP5Is12RQwFvKvExnqg1ziTy5PhfCDAFdR10pXskrD0cHH204rPc-0ewdd2hCL1mz40"> Link </a> |
| Temparature Sensor | Detecting between sidewalk and road | $14.99 | <a href="https://www.amazon.com/BOJACK-Temperature-Sensors-TMP36GZ-Precision/dp/B08BFY91ZW/ref=sr_1_1?crid=31Y6Y8IX9R3TM&dib=eyJ2IjoiMSJ9.VzayGqBKyq8z4l9agIQLpSOKdW4RxWLf8oRlmh7bJhHGjHj071QN20LucGBJIEps.4XaoDQR0tDC2HLOzaeTze-e1Ql7xXOdd3zRIyRnSMzc&dib_tag=se&keywords=BOJACK+TMP36&qid=1722014155&sprefix=bojack+tmp36%2Caps%2C60&sr=8-1"> Link </a> |
| Speaker | Amplifying sound | $6.99 | <a href="https://www.amazon.com/Fielect-Magnet-Speaker-Internal-Diameter/dp/B0826YLV6C/ref=sr_1_1?crid=1S95IIG65GFFJ&dib=eyJ2IjoiMSJ9.7rVScTfTCbTp4d5573lwZ0PxeRLW61PQzlHBdpSWsVNiHE-9osFsZUmXRI4nItGthZ3RfzLZv7PPY5_Mv7m&th=1"> Link </a> |
| Color Recognition Sensor | Detecting Trash | $13.99 | <a href="https://www.amazon.com/Teyleten-Robot-TCS230-TCS3200-Recognition/dp/B08HH8QYF8/ref=sr_1_1?crid=1CBVXU3V285WN&dib=eyJ2IjoiMSJ9.Rh-iSB4O8efW_XG-LqWoS54NMIE1k6kB2W5WuA4Vat4QsZk_eAaSmWWaL-qTwbGXoMVgUDNUSf4YHj53Ot"> Link </a> |
| Box | To hold all of my components  | $8.99 | <a href="https://www.amazon.com/LeMotech-Junction-Dustproof-Waterproof-Electrical/dp/B07BPPKF2C/ref=sxin_31_pa_sp_phone_search_thematic_sspa?content-id=amzn1.sym.c98882c1-8429-4bde-81de-021904a36ced%3Aamzn1.sym.c98882c1-8429-4bde-81de-021904a36ced&crid=9V5JT9X982FV&cv_ct_cx=box%2Bfor%2Belectronics%2Barduino&dib=eyJ2IjoiMSJ9.0qJhcH-QmMCyoopqBd72DRuwgkjsFelbtUAFXMCh6xzGjHj071QN20LucGBJIEps.eTlhXfKvm5PY_TwZa_deYpiVTFrumUn-CxVYeU0IoZ0&dib_tag=se&keywords=box%2Bfor%2Belectronics%2Barduino&pd_rd_i=B07BPPKF2C&pd_rd_r=b3a9aef8-154d-4f7a-ab34-2894e7c9db37&pd_rd_w=bELqh&pd_rd_wg=VX8M6&pf_rd_p=c98882c1-8429-4bde-81de-021904a36ced&pf_rd_r=VXTZQ49J6B40DVVXJJC7&qid=1721827047&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sprefix=box%2Bfor%2Belextronics%2Barduino%2Caps%2C82&sr=1-1-364cf978-ce2a-480a-9bb0-bdb96faa0f61-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9waG9uZV9zZWFyY2hfdGhlbWF0aWM&th=1"> Link </a> |
| Serial Monitor | To display puddle depth  | $9.99 | <a href="https://www.amazon.com/GeeekPi-Interface-Adapter-Backlight-Raspberry/dp/B07QLRD3TM/ref=sr_1_1?crid=1MC4CXT2ZGUEW&dib=eyJ2IjoiMSJ9.i8X1MwCMXd2eXMMjd6xR9FzV04IDQG0iMWkR5okAmEOmZLHe6uas96B5zmNXTM3Nx3292irD2N-ZZgEroMEB1n--2hzqDVxTkBHAkqhj9qyl01GsqXo56PXSvYBuEhXifT3fxzEPgZwVMcjUnA_czYZvjnqbCeHK-J40rhp2jkpgO_7WEwyLmPOJxECIeEtp-NmjsXdu3ZT_kSSAfiSY_YTM-5PABDfwUFt1L6FhY_8.xOIFUBwMt6w3FHQQwgUlRnLuLC2ef-AHmegXEMGi8S0&dib_tag=se&keywords=arduino+serial+monitor&qid=1722519419&sprefix=arduino+serial+monitor%2Caps%2C73&sr=8-1"> Link </a> |



