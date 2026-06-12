---
title: "xorg.conf settings reset overnight"
date: 2011-05-05
forum: General Help
---

### Post by krapp on 2011-05-05
For some reason the preset resolution for my second display was reset overnight upon booting. I use the ATI Proprietary driver, and the closest resolution to my preferred one both in the Catalyst Center (amdcccle) and in the GNOME Monitor GTK utility is 1600x1200. I tried editing my xorg.conf to set it at 1680x1050, but the monitor doesn't reflect this edit, and still maintains a resolution of 1600x1200 even after rebooting. Also, neither the Monitor settings manager nor the Catalyst Center offer 1680x1050 as an option even though my xorg.conf specifies it as the preferred resolution.

My xorg.conf:

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1600 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "ATI"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2966 2966
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I tried--```
xrandr --addmode CRT1 1680x1050
``` --to no avail.

xrandr reading:

```
xrandr
Screen 0: minimum 320 x 200, current 2966 x 1200, maximum 2966 x 2966
LVDS connected 1366x768+1600+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   1024x600       60.0  
   800x600        60.0  
   800x480        60.0  
   640x480        60.0  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   1024x600       60.0  
   800x600        60.3  
   800x480        60.0  
   720x480        60.0  
   640x480        59.9  

```

The monitor I am trying to troubleshoot is a LCD Samsung display. It's being called a CRT1, is that a problem? Perhaps it should be called DFP1, which seems to be disconnected?

What's the magic phrase that I have to enter in the terminal to fix this annoying problem, which has never occurred before?  :D

---

