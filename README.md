# EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython


 
## NAME: Thejaswini D

## DEPARTMENT: B.E.CSE(IoT)

## ROLL NO: 212223110059

## DATE OF EXPERIMENT: 11.02.2026

## AIM

To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED

Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

## THEORY



FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

WORKING PRINCIPLE

The switches are connected as inputs to GPIO pins of the Pico.

The LEDs are connected as outputs.

A MicroPython script reads the switch states and controls the LEDs accordingly.

### CIRCUIT DIAGRAM
 ![image](https://github.com/user-attachments/assets/1c7234b9-5041-4156-94b8-0b846adb6b8e)
    Figure-01 circuit diagram of digital input interface 


Connect switch 1 to GP2 and switch 2 to GP3.

Connect LED 1 to GP14 via a 330Ω resistor.

Connect LED 2 to GP17 via a 330Ω resistor.

Connect the other terminals of the switches to GND.

## PROGRAM (MicroPython)
### EXPERIMENT 2A
```
from machine import Pin
from time import sleep

print("Welcome Pi Pico")

# Switches with internal pull-ups
switch1 = Pin(2, Pin.IN, Pin.PULL_UP)
switch2 = Pin(3, Pin.IN, Pin.PULL_UP)

# LEDs
led1 = Pin(15, Pin.OUT)
led2 = Pin(16, Pin.OUT)

while True:
    sw1_state = switch1.value()  # 0 when pressed, 1 when released
    sw2_state = switch2.value()
    
    print("Switch 1 state:", sw1_state)
    print("Switch 2 state:", sw2_state)
    
    # Turn off LEDs by default
    led1.value(0)
    led2.value(0)
    
    if sw1_state == 1 and sw2_state == 1:
        # Both pressed -> both LEDs off
        led1.value(0)
        led2.value(0)
    elif sw1_state == 1:
        # Only switch1 pressed -> blink led1
        led1.value(0)
        sleep(0.5)
        led1.value(1)
    elif sw2_state == 1:
        # Only switch2 pressed -> blink led2
        led2.value(0)
        sleep(0.5)
        led2.value(1)
    
    sleep(0.1)
```
### EXPERIMENT 2B
```
from machine import Pin
import time
print("Pi Pico")
led1 = Pin(0, Pin.OUT)
led2 = Pin(3, Pin.OUT)
led3 = Pin(6, Pin.OUT)
buzzer=Pin(15,Pin.OUT)
while True:
    led1.value(1) 
    print("LED is ON")
    time.sleep(1) 
    led1.value(0)  
    print("LED is OFF")
    time.sleep(1)
    led2.value(1) 
    print("LED is ON")
    time.sleep(1) 
    led2.value(0)  
    print("LED is OFF")
    time.sleep(1)
    led3.value(1) 
    print("LED is ON")
    time.sleep(1) 
    led3.value(0)  
    print("LED is OFF")
    time.sleep(1)
    buzzer.value(1) 
    print("Buzzer is ON")
    time.sleep(1) 
    buzzer.value(0)  
    print("Buzzer is OFF")
    time.sleep(1)
```

## OUTPUT
### EXPERIMENT 2A

<img width="989" height="806" alt="image" src="https://github.com/user-attachments/assets/6410821d-9b16-41a6-b304-9109b4b20a7b" />

<img width="964" height="791" alt="image" src="https://github.com/user-attachments/assets/0dec0d60-94b9-401a-9f45-c2b3b55dff26" />

<img width="1010" height="796" alt="image" src="https://github.com/user-attachments/assets/9729ac54-8b4f-4177-a3b2-90bcab0107a6" />

<img width="994" height="806" alt="image" src="https://github.com/user-attachments/assets/21592266-245c-4880-b990-feafcc72522b" />

### EXPERIMENT 2B
<img width="784" height="807" alt="Screenshot 2026-02-11 113701" src="https://github.com/user-attachments/assets/0610851d-c0b5-4cc1-8216-fbc28443ce03" />

<img width="820" height="716" alt="Screenshot 2026-02-11 113727" src="https://github.com/user-attachments/assets/88b36b83-b560-4d28-bd49-31e7345b8ba5" />

<img width="814" height="716" alt="Screenshot 2026-02-11 113746" src="https://github.com/user-attachments/assets/4149cac9-f405-4327-a170-51b364576c21" />

<img width="857" height="707" alt="Screenshot 2026-02-11 113806" src="https://github.com/user-attachments/assets/fef80a2c-11cc-4cb8-a0a1-b2f0ab152f82" />

## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

