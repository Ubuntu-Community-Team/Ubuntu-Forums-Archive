---
title: "My system doesnt like fglrx!!"
date: 2006-04-15
forum: General Help
---

### Post by StalfoS on 2006-04-15
I am running 64-bit ubuntu breezy with a radeon 9600.  I cant get the fglrx drivers to work!!!  Please help!
Here are some lines from my Xorg.0.log file:

[INDENT](II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "xtrap"
(II) Loading /usr/X11R6/lib/modules/extensions/libxtrap.a
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DEC-XTRAP
(II) LoadModule: "fglrx"
(WW) Warning, couldn't open module fglrx
(II) UnloadModule: "fglrx"
(EE) Failed to load module "fglrx" (module does not exist, 0)
[/INDENT]

---

### Post by StalfoS on 2006-04-16
Well..  It seems that I did not install it correctly.  Not sure exactly what I did wrong but I fiddled around a bit more and now it is working....    except....


...my TV-out picture is black and white, and flickering up and down.  At first guess I would think that it is a vertical refresh rate problem, but nothing I change in xorg.conf seems to make any difference.  Any ideas?

---

### Post by Mr Fat Bat on 2006-04-17
I'm also having a hell of a time getting fglrx to work.  I have it working at home, but it's a "no can do" so far on my work box with Dell 1907fp monitor, running on an ATI x300 card.

I've tried just about every forum idea I have come across.

---

### Post by StalfoS on 2006-04-18
I am very frustrated with the ATI fglrx driver.  I can not, for the life of me, get the TV-out to display properly.  

I am pretty sure that I have tried every possible setting in my xorg.conf file, and I can only conclude that it is a driver problem.  Here is th 'device' section:

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "fglrx"
	Option	    "TVStandard" "YUV"
	Option	    "TVOutFormat" "SVIDEO"
	Option	    "VideoOverlay" "on"
	Option 	    "StereoSyncEnable" "1"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "Centermode" "off"
	Option	    "DesktopSetup" "clone"
	Option	    "ForceMonitors" "tv"
	Option	    "TVFormat" "NTSC-M"
	Option	    "UseInternalAGPGART" "off"
	Option	    "VRefresh2" "60"
	Option	    "Mode" "1600x1200,1280x1024,1024x768,800x600,640x480"
	Option	    "Mode2" "1024x768,800x600,640x480"
	BusID       "PCI:1:0:0"
	Screen	    0
EndSection

It seems that the the screen and monitor setting dont have much effect byt I have also defined to screens, 2 monitor, etc  Also having another device section for the tv out doesnt seeem to make a difference.

All I want is for it to clone the video overlay on the TV screen.  It works on my windows install!

---

