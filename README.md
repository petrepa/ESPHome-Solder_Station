# ESPHome Solder Station
### This is a poorly documented project, I am sorry for that, but I think the idea and the practicallity of such a setup is too good to not be shared

![iron_deployed](https://github.com/petrepa/ESPHome-Solder_Station/blob/master/Images/iron_deploy.gif)

This projects gives you four schuko sockets you can controll though [Home Assistant](https://home-assistant.io) with [ESPHome](https://esphome.io/). 

In addition to power controll, you have a DHT sensor for temperature and humidity, and a binary indication for whether or not the soldering iron is docked in it's stand.

![collage](https://github.com/petrepa/ESPHome-Solder_Station/blob/master/Images/collage.jpg)

This enables us to make nifty automations making the use of the soldering station feel more exclusive. 

This happens when I deploy the soldering iron from its stand:
- The soldering iron automatically turns on and starts heating
- The lights above the desk turns on
- The soldering fan turns on

Whats connected to my station:
1. Soldering Iron
2. Soldering Fan
3. Glue Gun
4. _Not anything particulary at the moment_

The glue gun has its own stand 

## How
Using a NODEMCU-32S since it has a lot of digital GPIO.

Main concepts:
- The shucko sockets are connected to a four channel [relay breakoutboard](https://esphome.io/cookbook/relay.html?highlight=relay)
- [DHT sensor](https://esphome.io/components/sensor/dht.html?highlight=dht) connected to GPIO ports. Remember the resistor!
- The soldering iron dock have a wire screwed into it. This wire is connected to one of the MCUs [GPIO pins](https://esphome.io/components/binary_sensor/gpio.html?highlight=gpio), while the MCUs ground is connected to earth. Since the iron is connected to earth through the soldering station, the GPIO pin will be pulled to the earth when the iron is docked, and this can be read out binary from the pin.
- Using a USB wall adapter to provide 5V to the MCU and relay breakout board from 230V. This enables you to only connect the entire box to the wall using one power cord.
- Glue Gun with it's [own stand](https://www.thingiverse.com/thing:4578044) and an embedded push button which tells if the gun is docked or not. Using [GPIO pins](https://esphome.io/components/binary_sensor/gpio.html?highlight=gpio). 

![glue_gun](https://github.com/petrepa/ESPHome-Solder_Station/blob/master/Images/glue_gun_collage.png)
