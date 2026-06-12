---
title: "can not change res"
date: 2009-12-01
forum: General Help
---

### Post by starcraftmaster on 2009-12-01
hey guys
i just got ubuntu 9.10(used to have 9.4 which worked great but fdisk did something and i just got 9.10 because its new) but i can not change the resolution of the screen
i only got these two res:640x480 and 320x240


graphics card : nvidia geforce 4 mx
screen Viewsonic va702
max screen can go:1024x1280 max. graphics card can go : 2014 x ?forget

Nvidia driver:96.43.13 proprietary

please help

xorg.conf file
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
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

### Post by ed-koala on 2009-12-01
Have you enabled the restricted drivers?  Ststem - Administration - Hardware Drivers.

---

### Post by starcraftmaster on 2009-12-01
yes
also tried sudo dpkg-reconfigure xserver-org
did not work

---

### Post by Gene Rodgers on 2009-12-02
> **starcraftmaster said:**
> yes
also tried sudo dpkg-reconfigure xserver-org
did not work

Try installing gnome-control-center and screen-resolution-extra with the package manager. Look in the System, Administration, and Hardware Drivers and install the Nvidia driver. Then reboot to let all take effect.:popcorn:

---

### Post by starcraftmaster on 2009-12-03
Did that.
Still got the problem.

Where are Ubuntu 9.10 updates kept ? Am just going to reinstall.(need to any way got better harddrive now)

---

### Post by starcraftmaster on 2009-12-04
come on i need this fixed fast!

---

### Post by starcraftmaster on 2009-12-04
:(

---

### Post by starcraftmaster on 2009-12-05
Come on!!!!!!

---

