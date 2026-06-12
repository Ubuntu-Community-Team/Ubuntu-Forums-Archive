---
title: "Asus P4S533-MX Motherboard Video Card"
date: 2009-08-04
forum: General Help
---

### Post by tmogeem on 2009-08-04
hello everybody,

I have an old desktop PC and i thought why not delete windows and install Ubuntu instead .. Thats what i did and everything is working fin except for the graphics card SiS650 .. the windows drivers CD already has linux drivers for the graphics card but i think its for redhat only .. im not sure coz im not yet an advanced linux user .. so this is what they r saying to install the graphics driver

sis_drv.o-410 is for X server 4.1.0 (Redhat 7.2)
sis_drv.0-402 is for X server 4.0.2 (Redhat 7.0)
Installation Guide
install Redhat 7.2 or 7.0
cp sis_drv.o-410 or sis_drv.o-402 to /usr/X11R6/lib/modules/drivers/sis_drv.o
make sure the /etc/X11/XF86Config file have the correct "driver" section.
Drivers "sis"
Startx

how can i do all the above on Ubuntu? im using Ubuntu 9.04 Jaunty Jackalope ..

the reason i want to do this is bcoz the windows open, close, minimize and maximize very slowly. Plus the scrolling on any window is very slow .. and i suspect its the graphics card since i have 2 GB of RAM installed ..

one more thing, my xorg.conf file is empty ..

please if anyone could help me in configuring the graphics card driver, don't hinder your self from speaking out :D

Thank you

---

### Post by dcstar on 2009-08-05
> **tmogeem said:**
> hello everybody,

I have an old desktop PC and i thought why not delete windows and install Ubuntu instead .. Thats what i did and everything is working fin except for the graphics card SiS650 .. the windows drivers CD already has linux drivers for the graphics card but i think its for redhat only .. im not sure coz im not yet an advanced linux user .. so this is what they r saying to install the graphics driver

sis_drv.o-410 is for X server 4.1.0 (Redhat 7.2)
..........
please if anyone could help me in configuring the graphics card driver, don't hinder your self from speaking out :D

Thank you

Some graphics cards have little or no Linux support because the manufacturer will not provide the source code, this is probably one of them.

Buy a cheap Nvidia or ATI card and things may well improve.

---

### Post by tmogeem on 2009-08-05
> **dcstar said:**
> Some graphics cards have little or no Linux support because the manufacturer will not provide the source code, this is probably one of them.

Buy a cheap Nvidia or ATI card and things may well improve.

ya that's my plan if i couldn't solve this ..

thank you though :)

---

