---
title: "How do i get my video driver so i can get CompizFusion?"
date: 2010-01-14
forum: General Help
---

### Post by marcocervantes on 2010-01-14
I have a Dell Inspiron 1501 and have moved to Ubuntu 9.10 Karmic Koala. I want to get CompizFusion running just to make my laptop even more cool, but since im new (fairly) to ubuntu, i want to know if someone else has done it, because i dont want to go and mess it all up. Has someone done it?

---

### Post by mikewhatever on 2010-01-14
What kind of video driver do you have? Is it a custom compiled package of some kind?

---

### Post by renoman19 on 2010-01-14
I'm not sure if this fits to your system but dell says your system has a ATI IGP 1150 Graphics processor, ATI Has a driver for the 1250 and the whole xpress series, i wasn't so far able to find a driver for Linux for that laptop, I've never had this problem with my system, ubuntu has always found proprietary drivers for my computer and most the time worked. I wasn't able to find the information about the graphics but by guessing i don't think your graphics processor can handle much so i would be careful when using compiz. hope this helps.
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

---

### Post by marcocervantes on 2010-01-14
this is the video card i have "ATI Technologies Inc RS482 [Radeon Xpress 200M]" This was given to me by my terminal using this code"lspci -nn | grep VGA" and Ubuntu says :

"
All these cards and derivatives have good 3D acceleration support 

9500 / R300 based cards
9600 / rv350 or rv360 based cards
9700 / R300 based cards
9800 / R350 or R360 based cards
X300 / rv370 based cards
X600 / rv380 based cards
X700 / rv410 based cards
X800 / R420 or R423 or R430 or R480 based cards
X850 / R480 or R481 based cards
X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards
Xpress 200 / RS480 IGP
Xpress 200 / RS482 IGP for Intel
Xpress 200M / RS482 IGP
Xpress 1100 / RS482 IGP
Xpress 1150 / RS485 IGP
Xpress 1200 / AMD 690V / RS690C IGP
Xpress 1200 / AMD M690V / RS690MC IGP
Xpress 1250 / AMD 690G / RS690 IGP
Xpress 1250 / AMD M690 / RS690M IGP
Xpress 1250 / AMD 690G / RS600 IGP for Intel
Xpress 1270 / AMD M690T / RS690T IGP

"

I just want to know how i get CompizFusion running. Or do i need the OpenSource driver?

---

### Post by skymera on 2010-01-14
I run Ubuntu on my mum's 1501 couple years back. It indeed has a Xpress X1150 ATi chip.

Compiz run really bad and choppy even wobbily windows as far as i can remember.

Not sure what ATi's stance on Linux drivers is at the moment.

Try to install the driver using ENVY. It's in the repos and it's worked perfect for me every time (Nvidia 7900GS, 8800GT, GTX260 and ATi HD4870). Give it a try.

---

### Post by mick222 on 2010-01-14
The propiatary drivers no longer work as you probably know, but you could try the xorg-edgers drivers I installed them on my computer and they seem to work fine I can get the cube and compiz running .

> 

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 
  
Add the repositories to your software source, select mark all upgrades and synaptic should install the new drivers. These are experimental drivers so be careful. There is a link to more stable drivers but less up to date on the xorg-edgers launchpad page [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)  . Hope this helps

---

