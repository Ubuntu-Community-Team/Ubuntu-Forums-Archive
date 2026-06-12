---
title: "xorg.conf, dual head, two sessions"
date: 2006-03-05
forum: General Help
---

### Post by BlueNoteMKVI on 2006-03-05
I just inherited a dual-head graphics card and I'm itching to get it working the way I want.  I think I'm close, very close...but not quite there yet.

What I want, the ideal situation, would be two monitors that are independent but can share information.  What I mean is the ability to view desktop 1 on monitor 1 and desktop 2 on monitor 2, but send a window from 1 to 2 and have it pop up on the second monitor.  I want both monitors to use the same keyboard and mouse.  If I were able to copy-paste from one to the other I would be incredibly excited.

I've played around with some advice from various places and managed to get two different setups working, but neither of them are exactly what I'm looking for.  I can get a big desktop across both monitors, and that's cool, but not what I'm looking for.  Could be useful at times.  Currently I have two independent monitors sharing a keyboard and mouse but they are two completely different sessions.  I cannot move a window from monitor 1 to monitor 2.  Monitor 1 is the same KDE setup that I've been looking at, but monitor 2 is a new session that looks like it's the default KDE setup.

Here is my current xorg.conf:


```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen 0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY) - second head"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"GDM-5410"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"GDM-5410-2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Monitor		"GDM-5410"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "ATI Technologies, Inc. Radeon 7000 VE (RV100 QY) - second head"
        Monitor         "GDM-5410-2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen" 0 0
	Screen 1	"Second Screen" RightOf "Default Screen"
#	Screen 1	"Default Screen" 1280 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

For completeness and anyone who finds this thread later, here's the xorg.conf for one big desktop that spans both monitors.

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option 		"MonitorLayout"	"TDMS,TDMS"
	Option		"MetaModes" "1280x1024-1280x1024"
	Option		"MergedFB" "true"
	Option		"CRT2Position" "RightOf"
	Option		"OverlayOnCRT2" "on"
	Option		"MergedXineramaCRT2IsScreen0" "False"
EndSection

Section "Monitor"
	Identifier	"GDM-5410"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"GDM-5410-2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Monitor		"GDM-5410"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
        Monitor         "GDM-5410-2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen" 0 0
#	Screen 1	"Second Screen" RightOf "Default Screen"
	Screen 1	"Default Screen" 1280 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

What do I need to put in there for the setup I described?  Is it possible?  If not, how do I make the second monitor use my existing KDE settings?

---

### Post by incubus on 2006-03-05
Talk to Prosperos, I think he just went through the same process.

[http://www.ubuntuforums.org/showthread.php?t=139692]("http://www.ubuntuforums.org/showthread.php?t=139692")

I posted a link to an article there that could take you to the right direction.

incubus

---

### Post by Prospero2006 on 2006-03-05
I basically have the same desktop spanning two monitors. When I maximize a window it is aware of the monitor boundaries and only maximizes to that monitor. 

Here is my xorg.conf if you are interested:

```
 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
Screen 1
EndSection
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
Screen 0
EndSection
Section "Monitor"
	Identifier "Monitor0"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection
Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"Monitor0"
	DefaultDepth	24

Option "TwinView" "true"
Option "SecondMonitorHorizSync" "30-70"
Option "SecondMonitorVertRefresh" "50-120"
Option "MetaModes" "1152x864, 1152x864; 1152x864, 1152x864;"
Option "TwinViewOrientation" "LeftOf"
Option "Xinerama" "true"

	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection



EndSection
Section "Screen"
	Identifier	"screen0"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]1"
	Monitor		"Monitor1"
	DefaultDepth	24



	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
 Option "Xinerama" "ON"
 EndSection
 
 
 Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen	0	"screen0"
	Screen	1	"screen1"	RightOf	"screen0"
EndSection 



Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Randomskk on 2006-03-06
I have two heads, configured as two seperate things (I think it uses two framebuffers?) and while I can't send windows between them, they both have their own desktops, and I can copy/paste and use mouse and keyboard in both fine.

Being able to move windows would be nice, but I've found it somewhat redundant now. Learnt to live with it and all that :D

What got it setup really for me was fglrx's config tool. I can't remember the command, but look for the how to "latest ATI drivers" and I followed that, installed the drivers and ran the command listed as the one for complex setups. It got dual screens working nicely for me, with the exception of moving windows :D

---

