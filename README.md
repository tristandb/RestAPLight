# RestAPLight
Uses 433Mhz and relais, an Arduino and a web server to control lights and power.

#Requirements
* Ethercard EN28J60 module (not the shield)
* 433Mhz sender
* 433Mhz receiver
* Ethercard library (search Google for install)

## Connecting Arduino
###433 Mhz
Connect an 433Mhz sender to Arduino port 9. 
Connect an 433Mhz receiver to Arduino port 2.

### Connecting Ethercard
    VCC -   3.3V
    GND -    GND
    SCK - Pin 13
    SO  - Pin 12
    SI  - Pin 11
    CS  - Pin  8

# Controlling Lights
Lights can be controlled by opening lamp.html. Please note to specify the correct IP!

## Adding custom lights (433Mhz)
Discover lamps by uploading ShowReceivedCode to your Arduino. Open the serial and send a 433Mhz signal by pressing the remote. You'll get some numbers. Put that number in lamp.html like this:
    <button class="action expand success" lampaction="{discovered_id}"><i class="fa fa-power-off"></i>Name</button>
Now upload restapi to your Arduino and test the setup by opening lamp.html!

## Adding power (Arduino pins)
If your {discovered_id} is smaller than 50, the code will not be send with 433Mhz. Instead, you'll switch the pinout of your Arduino. This can be attached to a relais.

# Lamp.html
Lamp.html can be uploaded to a web server. It will send Ajax-request to port 80 of your Arduino. Please mind that if you forward ports to your Arduino, the connection is not secure and can be accessed from outside!
