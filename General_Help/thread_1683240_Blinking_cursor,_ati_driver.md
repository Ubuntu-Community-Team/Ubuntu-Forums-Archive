---
title: "Blinking cursor, ati driver"
date: 2011-02-07
forum: General Help
---

### Post by folone on 2011-02-07
I've seen lots of posts about cursor problems. I tried solutions from all, I could find, but neither helped. The cursor was distorted, but now it started blinking and disappearing. It drives me crazy. I would like to at least make it stop blinking (I could live with distortion). My xorg.conf:


```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "Configured Screen Device" 0 0
	Screen         "amdcccle-Screen[2]-0" RightOf "Configured Screen Device"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 330"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:2:0:0"
	Option "SWCursor" "true"
EndSection

Section "Screen"
	Identifier "Configured Screen Device"
	Device     "Configured Video Device"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3286 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3286 3286
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "yes"
EndSection

```

Someone please help!

---

### Post by folone on 2011-02-07
Edited:

```
Section "Extensions"
   Option       "Composite" "no"
EndSection
```

It would be great to have compiz enabled, but my eyes really hurt.

---

### Post by clhsharky on 2011-02-07
folone


More info please?

What video chip?

How did you install fglrx(ubuntu installer,ATI installer)?


Sharky

---

