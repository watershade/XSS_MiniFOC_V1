# XSS MiniFOC Project
[中文版](README_zh.md)

## 1. Introduction
This Project provides a simple , small-size and cheap FOC PCB solution. You can use this solution to test your FOC algorithm. The purpose of this design is to serve as the FOC drive for each motor of the four-wheel drive robot car.
Consider the cost of it, I will choose STM32G0 series as my target MCU. In this version, I will try to use STM32G070RBT6 which have 36 kBytes RAM and 128 kBytes Flash. 
Normally, the resources of this MCU is limited for complex FOC application. But it should be enough for simple FOC usage. I want to design a FOC board with CAN-BUS/CAN FD BUS interfaces. But this MCU don't have one. STM32G0B1 is better but more expensive. I may consider it or STM32G431 in next larger-size version. But those two series is more expensive. For a mini board, The CAN transceiver circuit will occupy a larger board size. RX232/485 interfaces have the same problem. If I want to connect several MiniFOC boards with Main Controller，I have to to find a way to cascade them. So I will try to use SPI daisy chain method to fulfill it. The board will provide two 3pin interfaces to achieve cascading. I2C can also be used to connect many nodes together. But I don't like it because it is easy to generate deadlock problem.
Consider the BLDC geared motor what I have acquired, I designed the voltage of the board to be 24V. The maximum current should consider to be 2.5A because the current of cheap BLDC I can get easily(not include Car model motor and flight control motor) is under 2A.

## 2. Hardware Selection
