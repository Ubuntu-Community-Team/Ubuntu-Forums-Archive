---
title: "Ubuntu 10.04 LTS - Dual monitor works only sometimes (ATI multi-desktop)"
date: 2011-05-19
forum: General Help
---

### Post by Botondus on 2011-05-19
I've been using my laptop with an external LCD monitor attached to it at work (Philips 201E). And at home with a different external monitor (Samsung 2032BW).
I have an ATI graphics card (HD3450), with Ati Catalyst drivers enabled and I'm using the Single display desktop (Multi-Desktop) seeting. At work I have the external monitor on the left and laptop on the right, while at home the other way around. 
So when I switch between the two setups, I just needed to go to Ati Catalyst Control Center, change the order of the displays, change the resolution (Home - 1680x1050, Work - 1440x900), reboot and it was all fine.

But since a while it doesn't work properly anymore:

At home it *still* works fine.
At work it doesn't work. Sometimes it works for some reason, after a few resolution/setting changes in ACCC and reboots... it's very strange and annoying.

Does anyone have any idea for fixing it? I've uninstalled and reinstalled the ATI restricted drivers and that seemed to make it work initially, but it still works just sometimes.

This is my xorg.conf currently:

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[6]-0" 0 0
	Screen         "amdcccle-Screen[6]-1" 1280 0
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
	Option	    "PreferredMode" "1280x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1440x900"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[6]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:6:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[6]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:6:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2560 1024
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[6]-0"
	Device     "amdcccle-Device[6]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[6]-1"
	Device     "amdcccle-Device[6]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Botondus on 2011-05-21
Any ideas on diagnosing/fixing this? 
Been struggling with it since some time.

Apparently if I boot up the laptop at work without the external monitor attached, then attach it and restart after that and then go into settings to set resolution/position and reboot again it seems to work. But still pretty strange,.

---

