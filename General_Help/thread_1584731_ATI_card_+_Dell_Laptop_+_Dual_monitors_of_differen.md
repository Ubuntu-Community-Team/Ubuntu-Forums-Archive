---
title: "ATI card + Dell Laptop + Dual monitors of different sizes has problem with cursor"
date: 2010-09-29
forum: General Help
---

### Post by ftaylor on 2010-09-29
Hello,

I have a Dell Studio 1558 laptop with a 1366x768 resolution screen. I have an LG flatron monitor with a 1600x900 resolution screen. The screen is connected to the laptop via a vga cable.

I am using the fglrx driver and have tried to configure the dual monitors through the ati catalyst user interface, aswell as through the gnome preferences>monitors user interface.

The problem is that I can move the mouse cursor over the top of the laptop screen. I think there is possibly some problem with a virtual desktop size of 900px high. Even in the gnome and ati monitor configuration UI's it shows a highlighted empty space above the placement of the laptop screen. This is very annoying as files on the desktop go north of the laptop screen when sorted by name, and the mouse just randomly disappears off the top of the screen sometimes.

Here is my xorg.conf, would really appreciate it if anyone can help me out here.

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableRandR12" "false"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "Mode2" "1280x768"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnableMonitor" "tmds1,lvds"
	Option	    "PairModes" "1600x900+1366x768"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-1"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   1600 900
		Depth     24
		Modes    "1600x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   1366 768
		Depth     24
		Modes    "1366x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2966 2966
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-1"
	Device     "amdcccle-Device[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by shutterbc on 2010-09-30
I think I have the same behavior as you.  Basically, all is well if both monitors are the same resolution, or more importantly the effective vertical display resolution is the same between monitors.

Currently I'm running on a Lenovo T410i (Intel graphics) with a 1440x900 LCD and a 1680x1050 external monitor.  What happens is I can move my cursor "below" the gnome task bar in invisible-desktop land on the smaller screen.

Is this the behavior that you see as well?  If so, I think this bug is relevant, not sure if it's a dupe of another (I'm almost certain it has to be, but I didn't find another yet):
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/652198](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/652198)

Hope this helps!

---

