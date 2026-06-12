---
title: "Ati drivers are sluggish?"
date: 2012-09-06
forum: General Help
---

### Post by luky1jay on 2012-09-06
Hey,

I installed the latest Ati CCC from following the guide at cchtml wiki. Flash videos and 3d games are still very slow, and I have a 7970.

```
jayden@jayden-ubuntu:~$ fglrxinfo
display: :0 screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.11762 Compatibility Profile Context
```

Anyone have any ideas on what to do here? Here is my xorg.conf

```
Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Monitor"
Identifier "0-DFP10"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
Option	 "PreferredMode" "1920x1080"
Option	 "TargetRefresh" "50"
Option	 "Position" "0 0"
Option	 "Rotate" "normal"
Option	 "Disable" "false"
EndSection

Section "Monitor"
Identifier "0-DFP9"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
Option	 "PreferredMode" "1920x1080"
Option	 "TargetRefresh" "60"
Option	 "Position" "1920 0"
Option	 "Rotate" "normal"
Option	 "Disable" "false"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option	 "Monitor-DFP10" "0-DFP10"
Option	 "Monitor-DFP9" "0-DFP9"
BusID "PCI:2:0:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Virtual 3840 1920
Depth 24
EndSubSection
EndSection
```


Would adding 'glx' to modules fix the problem by enabling OpenGL? Or will that break things?

---

### Post by luky1jay on 2012-09-07
I've changed my modules to this, it works a little better. Guild wars 2 still runs at 8fps. It's still very slow. Something's not right.

```
Section "Module"
	# direct rendering infrastructure which makes opengl go fast
	Load    "dri"
	# glx and glcore implement opengl
	Load    "glx"
	Load    "GLcore"
EndSection
```

---

### Post by Epodx64 on 2012-09-07
try grabbing the newest drivers from the x-swat/x-updates ppa use to help my Nvidia card out immensely.

---

### Post by luky1jay on 2012-09-07
That PPA lists nvidia drivers only :( I have an ATi card. :(

---

### Post by apochry on 2012-09-07
I assume you have installed the 12.8 Catalyst drivers, right?

How many fps do you get when you run```
fgl_glxgears
```?

---

### Post by luky1jay on 2012-09-08
Yes I was. I tried installing manually following CCHTML wiki and from the restricted drivers gui. Did a full re-install and all. Even the open source drivers were pretty much the same speed.

I was getting 200-250 fps in gears which is horrible considering people with cards much slower than mine can get over 500+

I have gone back to Windows for now. Let me know when Ubuntu is ready for home use and doesn't require a terminal to do everything ^^

Thanks for your help though guys, I appreciate it. I guess ATi just needs to pay more attention to Linux. Maybe after Steam is released on Ubuntu, there will be more of a demand for it. ):P

---

### Post by TenPlus1 on 2012-09-08
I tend not to use the additonal drivers way to install Ati graphics, instead I open terminal and type:

sudo apt-get install fglrx fglrx-amdcccle

then once it has installed type this to save xorg settings:

sudo aticonfig --initial

now reboot and you should have working Ati graphics and 3D...

---

### Post by luky1jay on 2012-09-08
> **TenPlus1 said:**
> I tend not to use the additonal drivers way to install Ati graphics, instead I open terminal and type:

sudo apt-get install fglrx fglrx-amdcccle

then once it has installed type this to save xorg settings:

sudo aticonfig --initial

now reboot and you should have working Ati graphics and 3D...
I tried that and got less than 300fps in glxgears :(

---

