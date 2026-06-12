---
title: "how to install graphic card drivers???"
date: 2009-10-31
forum: General Help
---

### Post by kart168 on 2009-10-31
hello ppl!


i'm new to ubuntu. after i had installed ubuntu 9.10 using wubi, i couldn't find a way to see if the graphic card( nvidia geforce fx 5500)  driver is already installed . So i have downloaded the driver from the nvidia site which mentions as "NVIDIA-Linux-x86-173.14.20-pkg1.run". but i don know how to run it or install it...pls help. or if there is a way to check for already installed drivers what shall i do ???

pls help

thanking you

---

### Post by PaulM1985 on 2009-10-31
Hi

I'm not great at graphics card stuff but I just clicked on "System" at the top of the screen, then on to "Administration", then to "Hardware Drivers". This found my graphics card and installed it for me.

Paul

---

### Post by realzippy on 2009-10-31
System/administration/hardware drivers

...there should be available/installed drivers for your graphics card.


but of course you can install your downloaded driver also:

Log out,press Alt+Ctrl+F2,a terminal opens,log in,type:

[B]sudo /etc/init.d/gdm stop
[/B]
**cd Desktop**

(assuming your driver downloaded to Desktop)

**sudo sh NVIDIA-Linux-x86-173.14.20-pkg1.run**

(need only to type "**sudo sh NV**" and hit Tab to autocomplete)

answer asked questions during installation with "yes"

**sudo reboot**


Thats it.

---

