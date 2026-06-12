---
title: "Unusually high clock freqs on radeon hd card when idle"
date: 2012-05-22
forum: General Help
---

### Post by hg088 on 2012-05-22
These are the readings i get:
Default Adapter - AMD Radeon HD 6800 Series 
Core (MHz) Memory (MHz)
**Current Clocks : 900 1050**
Current Peak : 900 1050
Configurable Peak Range : [775-1000] [1050-1250]
**GPU load : 0%**

hector@hector-desktop:~$ aticonfig --odgt

Default Adapter - AMD Radeon HD 6800 Series 
    **              Sensor 0: Temperature - 59.00 C**

And these are some readings i found in an overcloking blog:

DEFAULT settings ATI HD6870:
greenone@desktop#  aticonfig –odgt –adapter=all
Adapter 0 – AMD Radeon HD 6800 Series
**Sensor 0: Temperature – 39.00 C**
greenone@desktop:~$ aticonfig –odgc –adapter=all
Adapter 0 – AMD Radeon HD 6800 Series
Core (MHz) Memory (MHz)
**Current Clocks : 100 150**
Current Peak : 900 1050
Configurable Peak Range : [775-1000] [1050-1250]
GPU load : 1%

So my problem is that my card is always hot due to this high freqs, even when idle

---

### Post by hg088 on 2012-05-23
I found an acceptable solution to this problem ([http://superuser.com/questions/270431/over-underclock-5870-on-linux-without-limits]("http://superuser.com/questions/270431/over-underclock-5870-on-linux-without-limits"))

AMDOverdriveCtrl allowed me to set static clock speeds for my GPU so i set the clock to the speeds i read in windows and now the temps are equal. Now i have to run this on boot and dont have dymamic clocks but at least my temps are low

---

### Post by hg088 on 2012-05-24
Jmm, i found out that when i disabled my second monitor (using the catalyst driver) the frequencies and temperatures behave just like in windows :D

---

