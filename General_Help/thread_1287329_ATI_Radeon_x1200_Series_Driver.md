---
title: "ATI Radeon x1200 Series Driver"
date: 2009-10-10
forum: General Help
---

### Post by C_Bomb on 2009-10-10
Hey guys, I wanted to download my ATI Radeon x1200 series DRIVER from their main website..

But they don't have it in the list...look at the attachment pic.

Where can I get it? or can I download the x1300 series driver?

---

### Post by QIII on 2009-10-10
I believe your GPU has been unceremoniously and callously relegated to AMD/ATI's "legacy" graveyard.

They have some support for older cards in their 9.4 driver, but it will not work with the latest X.org.

You will probably have to continue to use the open source driver.

---

### Post by psycho5 on 2009-10-19
Okay I am trying to figure out what is the reason why I wasn't enable compiz for my video driver before, but now it is!  I have ati x1200 series onboard. According to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) the ati driver has good 3D accelerated support : 

> 
Accelerated 3D support (r300, r400 and r500 series)

All these cards and derivatives have good 3D acceleration support 
```

Xpress 1200 / AMD 690V / RS690C IGP
Xpress 1200 / AMD M690V / RS690MC IGP

```




And here's the info regarding my card from terminal : 

```

oj@oj-desktop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
oj@oj-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
oj@oj-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
oj@oj-desktop:~$
```

So now I enabled compiz and it started working. 

```

oj@oj-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1920x1080) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

So you shouldn't bother with ATI's independent driver. The one provided with Ubuntu works just fine for me. Using 9.04 64bit

---

