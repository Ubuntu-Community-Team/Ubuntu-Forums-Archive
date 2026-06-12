---
title: "No display when laptop not plugged into external monitor...."
date: 2011-01-25
forum: General Help
---

### Post by paulig2001 on 2011-01-25
I'm having a very odd problem in that when I boot up without my laptop plugged into an external monitor my display is blank, but when I boot up with a monitor plugged in I get multi-display just fine (i.e. there's obviously nothing wrong with the laptop screen).

I think something may have gone wrong in the Xord.conf file, but I'm a total newb so I've no clue how to fix it. I've posted the file below though if maybe someone here has an idea:


```

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1280 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual	3280 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3280 1080
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection
```

---

### Post by DeviantGuy on 2011-01-25
I thought this was the nessicary thread to put this post in rather than making a new thread
I'm having the same problem, slightly diffrent however. I can get Ubuntu to display the screen correctly. But when I tap just ONE key It changes the monitor setup (External monitor only, Laptop display, Both not Resolution). Is their a command I enter into the terminal? Like a sudo command?

---

