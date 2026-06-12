---
title: "custom xorg.conf troubles w/ laptop: no screen detected"
date: 2009-10-24
forum: General Help
---

### Post by Quarg on 2009-10-24
I have an xorg.conf file that I have been screwing with that now looks like this: 

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"inspiron"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
 Identifier "i965 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
 Driver "vesa"
 BusID  "PCI:00:02.0"
 Option "NoAccel" "true"
 Option "PciRetry" "true"
EndSection

Section "Screen"
 Identifier    "Main Screen"
 Device        "i965 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
 Monitor       "Main Monitor"
 DefaultDepth 16
 SubSection    "Display"
   Depth 1
   Modes       "1024x768_75.00"
 EndSubSection
EndSection

Section "Monitor"
 Identifier "Main Monitor"
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen "Main Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mounse"
EndSection


And when I start the X server by restarting or typing
$gdm

I get this error:

(shortened logfile:)

(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(EE) No devices detected

Fatal server error:
no screens found

I am using an HP Pavillion dv9500.

---

