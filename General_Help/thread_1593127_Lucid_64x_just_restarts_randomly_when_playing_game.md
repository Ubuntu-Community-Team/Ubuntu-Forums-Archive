---
title: "Lucid 64x just restarts randomly when playing games"
date: 2010-10-11
forum: General Help
---

### Post by Pithikos on 2010-10-11
I just have this weird problem where when I start playing some medium-intense game the computer just restarts randomly. I made a lot of search on it and even tested various things. I have been having this system for about a month and the problem appeared just one week ago. 
I am a big fan of "Spring: TA" and that's the easiest way to reproduce the problem, by playing that game(and the most annoying). The funny thing is that when I just start the game the gpu temperature raises very fast. If after some time the pc doesn't reboot on itself the temperature just gets lower and lower. 
I was suspicious that the problem had to do with temperature so I made some scripts and logged the temperatures in every instant time:

(keep in mind that last sentence is always half as the computer just restarts before the logging finishes)

**Log 1**
```
Mon Oct 11 01:44:41 CEST 2010
nVidia Geforce 8800GT
=> GPU temperature: 79C
=> Board temperature: 52C
CPU Fan Speed:    2205 RPM  (min =  600 RPM)
CPU Temperature:   +44.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +37.0°C  (high = +45.0°C, crit = +75.0°C)  

Mon Oct 11 01:44:41 CEST 2010
nVidia Geforce 8800GT
=> GPU temperature: 79C
=> Board temperature: 52C
CPU Fan Speed:    2205 RPM  (min =  600 RPM)
CPU Temperature:   +44.0°C  (high = +60.0°C, crit 
```**Log 2**
```
Mon Oct 11 01:52:20 CEST 2010
nVidia Geforce 8800GT
=> GPU temperature: -371C
CPU Fan Speed:    2227 RPM  (min =  600 RPM)
CPU Temperature:   +45.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +38.0°C  (high = +45.0°C, crit = +75.0°C)  

Mon Oct 11 01:52:20 CEST 2010
nVidia Geforce 8800GT
=> GPU temperature: 69C
=> Board temperature: 47C
CPU Fan Speed:    2227 RPM  (min =  600 RPM)
CPU Temperature:   +45
```**Log 3**
```
Mon Oct 11 02:30:00 CEST 2010
nVidia Geforce 8800GT
=> GPU temperature: 81C
=> Board temperature: 52C
CPU Fan Speed:    2184 RPM  (min =  600 RPM)
CPU Temperature:   +44.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +36.0°C  (high = +45.0°C, crit = +75.0°C)  

Mon Oct 11 02:30:01 CEST 2010
nVidia Geforce 8800GT
=> GPU temperature: 80C
=> Board temperature: 52C
CPU Fan Speed:    2184 RPM  (min =  600 RPM)
CPU Temperature:   +44.0°C  (high = +60.0°C
```
As you see the temperatures are really random so the problem hasnt anything to do with it. The GPU temperature at some points is bellow 70C as I was running the fan manually on 100% with nvclock to make sure it has nothing to do with temperature. I even opened my case in case there wasn't good airflow in the box but that didn't change much. Temperatures got not as high but there were still reboots.

I also suceeded reproducing the problem while having open 2 other games. The temperatures are still very random: 
**CPU - MB - GPU - Ambient**
44   37   69   45
45   38   70   45
48   38   77   50

Yesterday night I also run memtest 16 passes with 0 errors.
My system is:

[LIST]
[*]AMD Phenom || x4 3.4Ghz
[*]DDR3 4GB Lat-7
[*]ASUS M4A87TD
[*]Nvidia GT8800 512MB(which takes an extra cable from the psu)
[*]DVDRW-ROM
[*]HHD: PATA133 250GB
[*]PSU: 370W Trust (15Ampere on the 12V rail)
[/LIST]
Lucid x64, Gnome, Compiz disabled

I have also tryied running the system with just 2GB Ram, disabled 3 of the 4 CPU cores, took off the DVDRW-ROM, took off the one USB PCI I have installed. Was thinking that if it was a Wattage issue then while doing so would solve the problem but that didn't help.


Here's a brief list of what I tested:
[LIST]
[*]Ran without nvclock
[*]Spring low settings
[*]Different games
[*]Took off CD-ROM, 1 ram and disabled 3 of the 4 CPU Cores
[*]Ran Memtest
[*]Ran games with open case
[/LIST]
 
Anyone having any ideas? :(

---

### Post by hawthornso23 on 2010-10-11
No new ideas. You seen to have been quite thorough in investigating your problem. I hope someone here can help you.

However I would like to make one observation. To me, 370W looks a little wimpy for the hardware you are running. I tend to err on the side of caution when it comes to PSU wattage. I've just put together a fairly similar machine also with AMD Phenom II x4 , but I went with a 500W PSU to run it all. As the guy from home improvements would say, you can never have too much when it comes to power.

---

### Post by NCLI on 2010-10-11
Sounds like an unreliable/underpowered PSU. Try using [this]("http://extreme.outervision.com/psucalculatorlite.jsp") to figure out what you need..

---

### Post by Pithikos on 2010-10-11
from that test I got 350Watt so I am still in the limit. But I tryied some other test as well where I hit 400Watts.
Now I ordered som Corsair 550W and will see if that solves the problem :)

---

### Post by schuelaw on 2010-10-20
I don't know if this is related, but I have 10.04 on a collection of new 64 bit Dells in our mathlab.  All of them are exhibiting random reboot behavior.  I'm kind of stumped as to where to even begin to track this down.

On a side note, I just installed 10.04 64-bit on a class room computer and it too is now randomly rebooting.  It's a dell, but a different model.

---

### Post by Pithikos on 2010-10-20
Well can you give the computers' specifications?
Do they all reboot at the same time or each on its own?

Btw I solved my problem with just getting a new power supply. So maybe you could test with that?

---

### Post by envygeeks on 2010-10-20
Or you can stop jacking threads and make your own.

---

