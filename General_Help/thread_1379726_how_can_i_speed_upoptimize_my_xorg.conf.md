---
title: "how can i speed up/optimize my xorg.conf?"
date: 2010-01-12
forum: General Help
---

### Post by boriskarloffinablender on 2010-01-12
i'm stuck with software rasterizing atm on 9.10, on 8.04 i had indirect rendering which was faster. can any xorg ninjas please give me advice on how i can speed things up? :)

this is my current xorg.conf.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "glx"
	Load  "record"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync    58-62
        VertRefresh    75-117
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card0"
	Driver      "fbdev"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage 128 PR/PRO AGP 4x TMDS"
	BusID       "PCI:0:16:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by Xbehave on 2010-01-12
cut the line 	
```
Driver      "fbdev"
```
and install flgrx

---

### Post by boriskarloffinablender on 2010-01-12
> **Xbehave said:**
> cut the line 	
```
Driver      "fbdev"
```
and install flgrx

i'm pretty sure that there isnt a version of flgrx that will work with a rage 128.

---

### Post by Linuxforall on 2010-01-12
compiz-fusion icon has a tab for indirect rendering and loose binding which works quite well and is easy to implement.

---

### Post by cariboo on 2010-01-12
This is a support question, it doesn't belong in the Cafe. Moved to General Help.

---

### Post by Xbehave on 2010-01-12
> **boriskarloffinablender said:**
> i'm pretty sure that there isnt a version of flgrx that will work with a rage 128.
ok well then you'll want 
> Driver      "r128"   
[this]("http://linux.die.net/man/4/r128") may help but tbh i don't know if dri is supported for r128, switching from fbdev should speed you up a fair bit though.

---

### Post by boriskarloffinablender on 2010-01-12
> **Xbehave said:**
> ok well then you'll want 

[this]("http://linux.die.net/man/4/r128") may help but tbh i don't know if dri is supported for r128, switching from fbdev should speed you up a fair bit though.

i had to change r128 to fbdev to get xserver to start.

---

### Post by Xbehave on 2010-01-13
> **boriskarloffinablender said:**
> i had to change r128 to fbdev to get xserver to start.
what happens if you don't have an xorg.conf? e.g mv /etc/X11/xorg.conf{,~} it should switch back to r128 by default (if that works then the problem is one of the options doesn't work with r128.
perhaps there is a problem with the r128 driver, perhaps there is a fix in a newer version (xorg-edgers) or there is a binary module for it (ati website), tbh i don't know r128 drivers at all well i've only used nvidia,radeon and intel.

---

### Post by boriskarloffinablender on 2010-01-13
> **Xbehave said:**
> what happens if you don't have an xorg.conf? e.g mv /etc/X11/xorg.conf{,~} it should switch back to r128 by default (if that works then the problem is one of the options doesn't work with r128.
perhaps there is a problem with the r128 driver, perhaps there is a fix in a newer version (xorg-edgers) or there is a binary module for it (ati website), tbh i don't know r128 drivers at all well i've only used nvidia,radeon and intel.

without xorg.conf it uses fbdev but gets stuck at 256 colors. i just took a guess and generated Xorg -configure and swapped out r128 for fbdev as it was what the var log output said it had used without a xorg.conf. it worked and i modified the desktop depth afer googling how to do it. 

the strange thing is r128 worked fine on 8.04!

---

### Post by boriskarloffinablender on 2010-01-13
bump.

---

