---
title: "Black screen at login with Nvidia card"
date: 2009-12-12
forum: General Help
---

### Post by QuickFinder on 2009-12-12
Hey there. I have an nvidia graphics card. I've installed Karmic on my system, and I'm getting a black screen at the login (no signal). This has happened a few times before with previous releases, so I tried the same fix again: I created a xorg.conf file and replaced "nv" with "vesa" in the Device section, so that I could get to the GUI and then install the restricted drivers.

This time, though, it didn't work, and I've tried several fixes already with the same results. I'm stumped. I can get a root shell going in recovery mode, though, so let me know what information you need to help me figure this out. As before, I'd like to just activate vesa so that I can see what I'm doing.

Here's my xorg.conf file as it stands now:

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
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "dri2"
	Load  "glx"
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
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	VendorName  "nVidia Corporation"
	BoardName   "NV41.1 [GeForce 6800]"
	BusID       "PCI:4:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by aot2002 on 2009-12-12
did you see if it created a backup xorg.conf.backup ?

or 

sudo dpkg-reconfigure xserver-xorg

---

### Post by QuickFinder on 2009-12-12
Nope, no back-up. I created the xorg.conf file using

sudo X -configure

and then copied the file xorg.conf.new over to /etc/X11/xorg.conf. When that didn't work, I tried resetting the file using

sudo dpkg-reconfigure -phigh xserver-xorg

but to no avail.

---

### Post by QuickFinder on 2009-12-12
Sorry to bump this back up, but surely someone has an idea of what I can do to get vesa running.

---

### Post by wojox on 2009-12-12
This is about as vanilla as it gets:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by QuickFinder on 2009-12-13
The vanilla method returns a black screen, too.

---

### Post by wojox on 2009-12-13
Try this ( forgot the vesa driver ):

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

