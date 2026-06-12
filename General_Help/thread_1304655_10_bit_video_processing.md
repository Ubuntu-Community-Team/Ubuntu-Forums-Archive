---
title: "10 bit video processing"
date: 2009-10-29
forum: General Help
---

### Post by barath on 2009-10-29
Hi,
I use kubuntu 8.10 ati mobility radeon x2300 my xorg.conf looks like this


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection


Now my doubt is ,is my card capable of displaying 10 bits of RGB or only 8 bits? If its a 10 bit image processing pipe  how do I enable this feature? 

Thanks in advance.

---

### Post by cascade9 on 2009-10-29
Your running 24bit RGB. 

DefaultDepth     24
Depth     24

---

### Post by barath on 2009-10-30
> **cascade9 said:**
> Your running 24bit RGB. 

DefaultDepth     24
Depth     24

ok cascade9 can you please tell me how do i change it and does my graphics card(ati mobility radeon x2300) support 30bit RGB...

Regards,
Barath.

---

### Post by cascade9 on 2009-10-30
24 bit is as high as ubuntu goes, AFAIK. 

BTW, by '10 bit' did you mean 10 bit per colour channel? If you did, then you have only got 8 bit per channel.

---

### Post by barath on 2009-10-31
> **cascade9 said:**
> 24 bit is as high as ubuntu goes, AFAIK. 

BTW, by '10 bit' did you mean 10 bit per colour channel? If you did, then you have only got 8 bit per channel.

I found this content in a website

NEWS: 10 Bit color and openGL processing feature:
Latest ATi cards offer this very useful feature that it is well hidden inside fglrx but can be enabled now and really offers better quality and speed generally in the visual output (tested at HD 3450 and HD 3650 cards but I think all the new should be ok)! It is not mentioned to cause any problems so I give you the way to enable it. As root user in a terminal window give this command:
Code:
aticonfig --set-pcs-val=DDX,OGLFMTA2R10G10B10Enable,1

link [http://forum.compiz.org/showthread.php?t=6794](http://forum.compiz.org/showthread.php?t=6794)

Thought I would clarify it.....

Regards,
Barath.

---

