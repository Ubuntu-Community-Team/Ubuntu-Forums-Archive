---
title: "x driver problems and desktop graphics!"
date: 2009-07-06
forum: General Help
---

### Post by happydappyman on 2009-07-06
OK first i am new to ubuntu. K so my problem is when i click more effects it says desktop effects could not be enabled. so i looked at some forums and noticed most didn't seem to apply to my whole setup ok so i installed (tried to install) nvidia drivers and it says im using nvidia accelerated graphics driver (version 180). when i go to nvidia x service settings it says You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. also when i restart the computer it says something along the lines of-failed to initialize graphics something at pci 2:0:0 or something. now in other forums they posted their xorg.conf and thats another problem my ENTIRE file (without instructions is this,
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

btw i added Driver "nvidia" cause someone said to do that but it did nothing. 
now can someone pleeez help me with this! i have been around the forums for hours and cant fine anything specific to my computer especially the short file here.
i have ubuntu 9.04

---

### Post by happydappyman on 2009-07-06
YAY i got it remove the tv tuner card

---

