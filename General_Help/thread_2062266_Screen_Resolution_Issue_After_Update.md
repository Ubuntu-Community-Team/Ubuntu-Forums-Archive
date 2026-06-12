---
title: "Screen Resolution Issue After Update"
date: 2012-09-24
forum: General Help
---

### Post by marque on 2012-09-24
I have been using Ubuntu 12.04 LTS for several months and have had no major problems up to now.  A couple of days ago I updated the system using the Update Manager in the usual way.  This particular update group contained a new linux kernel image.

The trouble began when I kept getting messages about a broken package, so I used Synaptic to find and repair the broken package.  It was the new kernel image.

There are several issues but I will address the most problematic in this post. The screen resolution on my machine is stuck at 640x480.

Here are some basic info from my system.

xrandr tells me:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0* 

from xorg.conf:
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


basic system hardware:
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ × 2 
VESA: MCP77 Board - mcp78uo


I'm needing someone to give me some direction here.  Thanks.

---

### Post by doktorOblivion on 2012-09-24
I would suggest booting in recovery mode with networking.  Then perform an apt-get update, followed by installing the latest nvidia drivers, they may be out of sync.  This is probably what you should have:
```

~$ dpkg -l | grep nvidia
ii  nvidia-common                          1:0.2.44                                Find obsolete NVIDIA drivers
ii  nvidia-current                         295.40-0ubuntu1.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver

```

You may run the same command to find out what you have.  But this would be the first thing I would check.

---

### Post by marque on 2012-09-24
When I grep'ed for nvidia this is the result:

~$ dpkg -l | grep nvidia
ii  nvidia-common                          1:0.2.44                                Find obsolete NVIDIA drivers
ii  nvidia-current                         304.43-0ubuntu1~precise~xup1            NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        304.43-0ubuntu1~precise~xup1            Tool of configuring the NVIDIA graphics driver

Running the three commands that you suggested ran ok but the install told me that I already had the latest nvidia drivers.

Nothing has changed, still the same small screen resolution.

---

### Post by Manhi40 on 2012-09-24
I had a similar problem... 
> cvt 1200 800 (use your res)
> xrandr --newmode "1200x800_60.00"   78.00  1200 1264 1384 1568  800 803 813 831 -hsync +vsync
(use output from first command)
then, in display settings your new res should be there...
I think this might work for you, good luck...

---

