---
title: "Pls explain this error"
date: 2011-01-26
forum: General Help
---

### Post by migrate from windows on 2011-01-26
I have installed ubuntu 10.10 in my desktop with VGA compatible  controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset  Integrated Graphics Device (rev 03)

By default the VESA driver is enabled (No 3d or acceleration) Whenever I  try to manually enable the intel driver by editing the xorg.conf file  the system boots only to text mode (ctrl+alt+f7) also does not give GUI.  This is the error i see in the boot llog  pleas etell me what it means.

.....................

[    20.453] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.453] (II) Module intel: vendor="X.Org Foundation"
[    20.453]     compiled for 1.9.0, module version = 2.14.0
[    20.453]     Module class: X.Org Video Driver
[    20.453]     ABI class: X.Org Video Driver, version 8.0
[    20.453] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    20.454] (--) using VT number 7

[    20.472] (EE) No devices detected.
[    20.472] 
Fatal server error:
[    20.472] no screens found
[    20.472] 


Pls help

---

### Post by djeikyb on 2011-01-26
Are you sure the driver you're trying to use is for your card? You say you have an 82845G/GL, but when Xorg loads the driver and lists all the chipsets it's good for, yours isn't there.

EDIT:
I take that back. Just saw the [intellinuxgraphics.org]("http://intellinuxgraphics.org/documentation.html") page that says the short name of your chipset is 845G, which is indeed mentioned.

Did you ever install the intel driver? Maybe the one you currently have with your X server has been updated?
sudo apt-get install xserver-xorg-video-intel

Can you post your Xorg.conf?

---

### Post by migrate from windows on 2011-01-26
This is my simple xorg.conf file


Section "Device"
Identifier      "Configured Video Device"
Driver          "intel"
EndSection
Section "Monitor"
Identifier      "Configured Monitor"
EndSection
Section "Screen"
Identifier      "Default Screen"
Monitor         "Configured Monitor"
Device          "Configured Video Device"
EndSection

---

### Post by migrate from windows on 2011-01-26
I feel so stupid .....should I enter the name of the device in the place of "configured video device".......

Im very much new to linux....pls bear if my question is stupid.

---

### Post by djeikyb on 2011-01-26
(1) With the advent of I think 9.10, I've pretty much given up on editing Xorg directly. From what I understand, if you run these commands, you should automatically be running the intel drivers:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-intel
```

You'll need to restart X after this. Normally that would be ctl+alt+backspace, but Ubuntu borked this. I think you have to reboot. Since you're migrating from Windows this will be familiar.

(2) Run this command to find what driver you're using:
```
glxinfo | grep "renderer string"
```

(3) After trying the above and reporting back here (just so we're not jumping wildly around with multiple solutions, and end up not knowing what the heck we're doing), check this out, maybe it will help:

[http://www.ubuntugeek.com/ubuntu-10-04-lucid-lynx-and-intel-video-chipsets.html](http://www.ubuntugeek.com/ubuntu-10-04-lucid-lynx-and-intel-video-chipsets.html)

---

### Post by migrate from windows on 2011-01-27
> **djeikyb said:**
> (1) With the advent of I think 9.10, I've pretty much given up on editing Xorg directly. From what I understand, if you run these commands, you should automatically be running the intel drivers:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-intel
```You'll need to restart X after this. Normally that would be ctl+alt+backspace, but Ubuntu borked this. I think you have to reboot. Since you're migrating from Windows this will be familiar.

(2) Run this command to find what driver you're using:
```
glxinfo | grep "renderer string"
```(3) After trying the above and reporting back here (just so we're not jumping wildly around with multiple solutions, and end up not knowing what the heck we're doing), check this out, maybe it will help:

[http://www.ubuntugeek.com/ubuntu-10-04-lucid-lynx-and-intel-video-chipsets.html](http://www.ubuntugeek.com/ubuntu-10-04-lucid-lynx-and-intel-video-chipsets.html)

for sudo dpkg-reconfigure -phigh xserver-xorg 
there was no respone
for Sudo apt-get install xserver-xorg-video-intel[/code] 
it says the latest versions are already installed



2. the error i get is glxinfo not installed

pls help

---

### Post by maniandram on 2011-01-27
To install glxinfo run
```

sudo apt-get install mesa-utils

```

---

### Post by migrate from windows on 2011-01-27
Thnks istalled mesa utilities

this is what i get

srikanth@srikanth-desktop:~$ glxinfo | grep "renderer string"
OpenGL renderer string: Software Rasterizer

---

### Post by djeikyb on 2011-01-27
Just for kicks, try running (replace $USERNAME with your username)
```
sudo adduser $USERNAME video
```

Then run that glxinfo command again.

---

### Post by migrate from windows on 2011-01-28
It says username group video already exists...and same response glxinfo

---

### Post by djeikyb on 2011-01-28
Can you copy and paste from the terminal? That isn't output that I would expect from running that command.

---

### Post by migrate from windows on 2011-01-28
> **djeikyb said:**
> Can you copy and paste from the terminal? That isn't output that I would expect from running that command.


srikanth@srikanth-desktop:~$ sudo adduser $srikanth video
[sudo] password for srikanth: 
adduser: The group `video' already exists.

srikanth@srikanth-desktop:~$ glxinfo | grep "renderer string"
OpenGL renderer string: Software Rasterizer

---

### Post by robert shearer on 2011-01-28
try.....
```
sudo adduser srikanth video
```

---

### Post by migrate from windows on 2011-01-28
srikanth@srikanth-desktop:~$ sudo adduser srikanth video
[sudo] password for srikanth: 
Adding user `srikanth' to group `video' ...
Adding user srikanth to group video
Done.

srikanth@srikanth-desktop:~$ glxinfo | grep "renderer string"
OpenGL renderer string: Software Rasterizer
srikanth@srikanth-desktop:~$ 



The sam ething....  why my device is not getting detected ??????

---

