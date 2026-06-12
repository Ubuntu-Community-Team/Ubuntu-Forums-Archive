---
title: "Display Resolution increase for Ubuntu 9.10"
date: 2010-04-01
forum: General Help
---

### Post by chamalj on 2010-04-01
I have ubuntu 9.10 on my computer. I want to change the resolution to 1280x1024
following is my xorg.conf file copy

my monitor is NEC F17M02-R

Please help me to modiy it to give me the required resolution...
the Vga card is Nvidia FX5200.. thanking you for your precious time

.....................................................................

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

.......................................................................

I am so much tired with this resolution..
please help

---

