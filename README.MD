# TTGO-Camera-SSD1306-PIR-BME380
A rebuild of the development for the above board available at https://www.amazon.com/dp/B07X1W2PT3

![pic](image/1.jpg)

PressPage Entertainment Inc DBA PINGLEWARE

## Notice
This board incorporates many features that can used for a project to interact with people, like the Camera, OLED display and PIR sensor. The BME can provide weather and orientation stats. Additional features that could be included included a microphone and speaker inetrface to have real time audio streaming as well as a GPS monitoting.

The board uses the I2C protocol to communicate with multiple devics, and adding a microphone, speaker and GPS to the I2C bus will permit these extra features. Read more about I2C communication at https://learn.adafruit.com/circuitpython-basics-i2c-and-spi/i2c-devices.

## Build Modifications

- Now Arduino officially supports the camera, you need to update the Arduino to the latest, see [arduino-esp32](https://github.com/espressif/arduino-esp32/releases) for details.I am using the `1.0.1rc2` version when writing this code.
  
- In order to support BME280, I will use [Adafruit_BME280_Library](https://github.com/adafruit/Adafruit_BME280_Library), but this library conflicts with <esp_camera.h> and enters [Adafruit_BME280_Library](https://github.com/adafruit/Adafruit_BME280_Library) In Adafruit_BME280_Library change <Adafruit_BME280.h> --> 29 lines comment #include <Adafruit_Sensor.h>, BME280 this library does not use this header file, so comment out and no problem

- OLED requires [esp8266-oled-ssd1306](https://github.com/ThingPulse/esp8266-oled-ssd1306) library support
  
- Buttons require [OneButton](https://github.com/mathertel/OneButton) library support

## TTGO CAM PINS
| Name  | Num    |
| ----- | ------ |
| Y9    | 39     |
| Y8    | 36     |
| Y7    | 23     |
| Y6    | 18     |
| Y5    | 15     |
| Y4    | 4      |
| Y3    | 14     |
| Y2    | 5      |
| VSNC  | 27     |
| HREF  | 25     |
| PCLK  | 19     |
| PWD   | 26     |
| XCLK  | 32     |
| SIOD  | 13     |
| SIOC  | 12     |
| RESET | No use |

## Sensor & OLED
| Name | Num |
| ---- | --- |
| SDA  | 21  |
| SCL  | 22  |

## Other
| Name   | Num |
| ------ | --- |
| Button | 34  |
| PIR    | 33  |

* BUTTON : Reverse camera ,Currently the camera reverse color will not be normal, see [issues#9](https://github.com/espressif/esp32-camera/issues/9)
  
* PIR: Detecting human motion and will display the first screen



## Test Video
[YouTube](https://www.youtube.com/watch?v=CibcsmurTbo)

# MCP3245 Single Channel Analog to I2C
![Arduino Nano MCP3425 I2C Analog to Digital Converter Tutorial](https://www.youtube.com/watch?v=8mtNd0gtG8M)

Using an Analog to I2C for receiving microphone audio input

# I2C to Analog
See https://electronics.stackexchange.com/questions/333/implementing-i2c-to-analog

Using I2C -> Analog for sending audio to a speaker

# NEO-6MV2 GPS Module
From the datasheet, the UART Interface at the output pins (Can use SPI ,I2C and USB by soldering pins to the chip core).

https://www.amazon.com/HiLetgo-GY-NEO6MV2-Controller-Ceramic-Antenna/dp/B01D1D0F5M/
