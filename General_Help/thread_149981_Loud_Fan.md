---
title: "Loud Fan"
date: 2006-03-25
forum: General Help
---

### Post by leemobile on 2006-03-25
Whenever I log into Ubuntu, I notice my CPU fan is noticeably louder.

I'm running on a dual boot, and whenever I log into Windows it's much much quieter.

My specs:

AMD64 3700+
eVGA 7800 GT PCI
EVGA nForce4 mother board.

Any clues on how I can throttle the fan down a bit?

Thanks.

---

### Post by hajk on 2006-03-26
Is the CPU fan power cable connected to the proper connector on the mobo? On my
own mobo it says "CPU PWR" in really tiny letters?

---

### Post by r4ik on 2006-03-26
Apperently youre CPU needs more cooling using Ubuntu.
I wouldnt go throttle it down at the risk to get the system overheated.
Just buy a silent fan.
Or look at your "top" command (no quotes please) in a terminal to pinpiont the usage.

---

### Post by leemobile on 2006-03-27
[QUOTE=r4ik]Apperently youre CPU needs more cooling using Ubuntu.
I wouldnt go throttle it down at the risk to get the system overheated.
Just buy a silent fan.
Or look at your "top" command (no quotes please) in a terminal to pinpiont the usage.[/QUOTE]

Whoops.  I opened my case and it's the video card fan that's obnoxiously loud, not the CPU fan.

I forgot that my video card has a fairly large fan on it. 
Apparently this is a problem for other users too, but a nvidia driver update should solve this.

Thanks for the support.

---

### Post by Jason_25 on 2006-03-27
lm-sensors is the universal fan and temperature tool.  It has to be installed and configured first.  [Here]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors") is a how-to.  BTW, I am running Ubuntu on 3 nforce 4 boards, 2 dfi and 1 chaintech without the issue you described.  The fans run the exact same no matter what.

---

### Post by Zooropa on 2006-03-27
I found Windows XP actually made my P4 overheat, but it was fine in Ubuntu.

On opening, I discovered one of the blades of my CPU fan was snapped :-|

---

### Post by stocker on 2006-03-27
How can one of your fan blades snap?

---

### Post by Zooropa on 2006-03-28
I wish I knew.

The only way I can think this is possible is if someone stuck something in it, or one of the many extra cables from the PSU got in it's way.

---

### Post by moe_syzlak on 2007-11-27
i edited my xorg.conf and made "AIGLX" "on" in server flags section. now my laptop doesn't sound like a blow dryer

---

### Post by moe_syzlak on 2007-11-27
i did like so:

# Xorg configuration created by livna-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics" "CorePointer"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules/extensions/nvidia"
	ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
	Option	    "Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "LPL"
	HorizSync    30.0 - 75.0
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce Go 7300"
	Option	    "Accel" "true"
	Option	    "AddARGBGLXVisuals" "True"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "RenderAccel" "true"
	Option	    "TwinView" "0"
	Option	    "metamodes" "1440x900 +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section DRI
Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

---

