---
title: "Controlling GPU Fan Speed"
date: 2010-10-20
forum: General Help
---

### Post by FinalShot on 2010-10-20
Out of curiosity, how can you control the fan speed?

---

### Post by jerrrys on 2010-10-21
how bout this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fan+speed+control&as_qdr=all&sa=Google+Search&lang=en#1044](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fan+speed+control&as_qdr=all&sa=Google+Search&lang=en#1044)

---

### Post by cascade9 on 2010-10-21
@ FinalShot- with ATI, I'm not to sure. With nVidia, nvclock will control the fans on at least some cards. 

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

> **jerrrys said:**
> how bout this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fan+speed+control&as_qdr=all&sa=Google+Search&lang=en#1044]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fan+speed+control&as_qdr=all&sa=Google+Search&lang=en#1044")

Nice try, most of the results are CPU fan speed though, not GPU fan speed.

---

### Post by jerrrys on 2010-10-21
oops, got to learn how to read one of these days

---

### Post by cascade9 on 2010-10-21
:lolflag:

---

### Post by FinalShot on 2010-10-24
Thanks but nvclock doesn't help, oh and I'm using a 9800GT if that helps.

---

### Post by cascade9 on 2010-10-24
nvclock wont let you change the fanspeed? 

The setting should be under 'hardware monitoring', you would need to enable fanspeed adjustments then play with the slider to affect the fanspeed.

---

### Post by FinalShot on 2010-10-24
Nope, it just has the temperature. And for the record, it is way off ( -386 Celsius ).

---

### Post by cascade9 on 2010-10-24
Odd. You should get something like this- 

[IMG]http://iyanovich.files.wordpress.com/2010/01/nvclock-fanspeed.png?w=480&h=274[/IMG]

BTW, does your nvidia drivers (nvidia-settings) have the same temprature error?

---

### Post by FinalShot on 2010-10-24
No, it has the correct temperature.

[img]http://img253.imageshack.us/img253/3940/nvclock.png[/img]

---

### Post by cascade9 on 2010-10-25
Very annoying. Looks like nvclock wont work to control your fanspeeds. :(

---

### Post by FinalShot on 2010-10-26
Hopefully someone else has the answer.

---

### Post by cascade9 on 2010-10-26
Its the only way I know of that will let you control the fanspeed on an nvidia card under linux. Apart from hardware controls of course. 

You could see if your card is recognised by nvclock. Go to a terminal, and the type- 

nvclock --info

You should get a readout like this- 

```
nvclock --info
-- General info --
Card:           nVidia Geforce 8600GT
Architecture:   G84 A2
PCI id:         0x402
GPU clock:      576.000 MHz
Bustype:        PCI-Express

-- Shader info --
Clock: 1296.000 MHz
Stream units: 32 (11b)
ROP units: 8 (11b)
-- Memory info --
Amount:         512 MB
Type:           128 bit DDR2
Clock:          399.600 MHz

-- PCI-Express info --
Current Rate:   16X
Maximum rate:   16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 65C
Fanspeed: 30.5%

-- VideoBios information --
Version: 60.84.59.00.00
Signon message: GV-NX86T512H F80  
Performance level 0: gpu 575MHz/shader 1300MHz/memory 400MHz/0.00V/100%
VID mask: 3
Voltage level 0: 1.20V, VID: 0
Voltage level 1: 1.32V, VID: 1
```

---

### Post by FinalShot on 2010-10-26
You know the program doesn't support "NV50/G8x/G9x/GT200".

```
scott@scott-desktop:~$ nvclock --info
Unhandled init script entry with id '&#65533;' at c9fa
-- General info --
Card:         nVidia Geforce 9800GT
Architecture:     G92 A2
PCI id:     0x614
GPU clock:     300.856 MHz
Bustype:     PCI-Express

-- Shader info --
Clock: 1350.000 MHz
Stream units: 112 (01111111b)
ROP units: 16 (1111b)
-- Memory info --
Amount:     1024 MB
Type:         256 bit DDR3
Clock:         300.856 MHz

-- PCI-Express info --
Current Rate:     16X
Maximum rate:     16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: -384C

-- VideoBios information --
Version: 62.92.84.00.06
Signon message: NVIDIA GeForce 9800 GT VGA BIOS
Performance level 0: gpu 300MHz/shader 600MHz/memory 300MHz/0.95V/100%
Performance level 1: gpu 550MHz/shader 1375MHz/memory 900MHz/1.05V/100%
VID mask: 3
Voltage level 0: 0.95V, VID: 0
Voltage level 1: 1.00V, VID: 2
Voltage level 2: 1.05V, VID: 3
```

---

### Post by cascade9 on 2010-10-27
> **FinalShot said:**
> You know the program doesn't support "NV50/G8x/G9x/GT200".

You know, it actually does- 

> NVClock 0.8 (beta4) offers support for the latest cards and improves functionality for current models like smartdimmer support for Geforce8/9 boards and fanspeed adjustment / temperature monitoring on most Geforce8/9/GT200 cards.

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

nvclock works just fine wiith my 8XXX video card (a 8600GT, I havent tried the 8400GS around here). 

It might not work with your card, but saying it doesnt support 8XXX/9XX/GT2XX is just wrong.

---

### Post by FinalShot on 2010-10-27
I've reached the limits of my patience with your level of incompetence.

---

### Post by cascade9 on 2010-10-28
Ever heard the saying' you'll catch more flies with honey than vinegar'?  

BTW, there is another way to change fanspeeds, just I dont ever recommend it. NiBiTor.

---

