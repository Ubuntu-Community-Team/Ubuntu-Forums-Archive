---
title: "i can not put the resolution above 640x480"
date: 2009-12-14
forum: General Help
---

### Post by starcraftmaster on 2009-12-14
hello
i got ubuntu 9.10 and i can not put the resolution above 640x480
this is really annoying
Card:geforce 4 mx 440 (leadtek)
lcd mointer:viewsonic va702


xorg.conf(seems smaller then ubuntu 9.04)

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "true"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by lewisforlife on 2009-12-14
Are there any drivers available for your video card in System-->Administration-->Hardware Drivers?

---

### Post by starcraftmaster on 2009-12-15
yes i already have the nvidia 93 drivers

---

### Post by Grenage on 2009-12-15
A lot of people are having luck putting modelines into their xorg.conf.

---

### Post by realzippy on 2009-12-15
> **starcraftmaster said:**
> yes i already have the nvidia 93 drivers

Install nvidia-settings:

**sudo apt-get install nvidia-settings**

---

