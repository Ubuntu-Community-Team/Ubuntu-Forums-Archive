---
title: "Strange Monitor Display Issue"
date: 2010-08-24
forum: General Help
---

### Post by gavinjb on 2010-08-24
Hi,

Just trying to configure my Sony Laptop with my Viewsonic VX2260 Monitor with Ubuntu 10.04 and getting strange results, hope someone can help.

In Windows 7 I had this configure with no problems but in Ubuntu as I mentioned I am having some strange issues!  I have installed the drivers for my ATI Mobility Radeon HD 4500 Series Graphics Card and everything seems to work, I have also configure it so that my Laptop Screen is off and the Monitor is set at top Res of 1920x1080 (same as in Windows 7), but where in Windows it filled the fI get a large black boarder around the screen (about 2-3 cm) and I cant work out why I am getting this and how to get the whole screen to be used, any ideas.

One thing I have noticed is that the Monitor is defined as unknown.

I have also included my xorg incase it can help.

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "50"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3286 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Thanks,


Gavin,

---

### Post by gavinjb on 2010-08-25
Just found this Topic, but it doesn't seem to help.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6660701]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6660701")

Also from looking at my Monitor spec from ViewSonics website and I can see that the resoultion looks correct in xorg, so I don't understnad why it is not using the full screen.

```

Type  	21.5” wide Color TFT Active Matrix LCD
Display Area 	47.50 cm (18.7") (H) × 26.67 cm (10.5"&#65289;(V) /54.6cm (21.5") diagonal
Optimum Resolution 	1920x1080 WUXGA
Contrast Ratio 	1000:1 (typ.) ; 20000:1 dynamic
Brightness 	300 cd/m² (typ.)
Viewing Angles 	170° (H), 160° (V)(CR&gE;10)
Response Time 	5ms (on/off) ; 2ms (G to G)
Light Source 	50,000 hrs. (typ)
Pixel Pitch 	0.248mm (H)×0.248mm (V)
Panel Surface 	Anti-Glare, Hard coating (3H)
Color Support 	16.2 M (6-bits + Hi FRC)

```

---

### Post by gavinjb on 2010-08-25
Update: found this article [http://www.cyberciti.biz/tips/howto-configure-viewsonic-vg1930wm-lcd-1440x900-display.html]("http://www.cyberciti.biz/tips/howto-configure-viewsonic-vg1930wm-lcd-1440x900-display.html")

and installled xresprobe, but when I run 

```

sudo ddcprobe

```

I get
```

Segmentation fault

```

and if I run 
```

sudo xresprobe

```

I get
```

id: 
res: 
freq: 
disptype: lcd/lvds

```

the strange thing with the monitor display is if I go to 1600x1200 it fills the monitor, but looks odd.

---

### Post by gavinjb on 2010-08-26
Can anyone help with this, this is all that is stopping me form making a complete switch over to Linux (finally) and I really want to get rid of my slow windows machine.

I just had a thought I tried rebooting with VGA connected to Monitor instead of HDMI and at the same res it fills the whole screen, I rebooted with HDMI and back to black border of no mans land around the usable screen.

I compared the xorg.conf from when VGA was connected to HDMI and nothing is different, so I don't understand why it is giving me this issue, mind you I have never understood xorg very well anyway!

Gavin,

---

### Post by QIII on 2010-08-26
Have you tried to use the Catalyst Control Center to make adjustments?  CCC is what generated your xorg.conf, which does not exist by default.

A couple of things concern me about your xorg.conf -- the "Screen" sections at the bottom.

The first appears to be trying to define the dimensions of a multiple screen setup, giving a virtual size with a very odd horizontal number.  It's probably being ignored, but it is weird.

The second "Screen" section doesn't contain a Modes line, which would look something like this after Depth in SubSection "Display":

```
Modes    "1920x1080"
```

Before you make changes, let me get home and check what it looks like on my machine with an AMD/ATI card.  But that one has dual monitors, so I might have to punt.

---

### Post by gavinjb on 2010-08-26
Thanks,

After I installed the ATI drivers I used CCC to disable my Laptop Monitor and set the res on my Monitor so the settings should be from CCC.

---

### Post by QIII on 2010-08-26
So you are now using an external monitor?

---

### Post by gavinjb on 2010-08-27
Yes, but I am getting that weird black border when I use the monitor at the reconmended res (1920x1080)

---

