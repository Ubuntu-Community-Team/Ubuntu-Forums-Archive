---
title: "Resolution &gt;.&lt;"
date: 2010-01-03
forum: General Help
---

### Post by zonefull on 2010-01-03
Hi guys :D
is theres a way to configure resolution to 1024*768 is ubuntu ?
as i recently got ubuntu on my pc and i only see on display the resolutions of 640*480
and 800*600 which is a pain for me >.< 
and how about the refreshing rate is it also possible 
thx in advance :)

---

### Post by starcraft.man on 2010-01-03
Limited resolution usually implies that you haven't installed graphics drivers for your card. Can you go to System > Admin > Hardware Drivers and enable the graphics driver for the nvidia/ati card you likely have. If nothings there, then your problly on intel and I not so great at fixing those up.

---

### Post by Grenage on 2010-01-03
If you can and do activate the drivers and it makes no difference, post back with your monitor make and model, and the output of the following command:

```
lspci | grep VGA
```

Sometimes people have issues with the display protocols not working between their computer and monitor, with that information, we can probably give you a config that will get the res you want.

---

### Post by zonefull on 2010-01-03
thx for reading its intel and i got this outbut 

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)


and i tried to follow this thread [http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)    but when i turn to GUI it dont accept my pw as ubuntu login and pw maybe cuz im not givin what it wants im nt realy sure

---

### Post by Grenage on 2010-01-05
You didn't post your monitor make and model, so I cannot check the sync values etc, but try replacing your current */etc/X11/xorg.conf* with the following:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "unknown"
ModelName "unknown"
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

As for the user/password issue, you might need to log in using single-user mode to change it.  There are some decent guides out there; just google something like *ubuntu forgot password*.

---

