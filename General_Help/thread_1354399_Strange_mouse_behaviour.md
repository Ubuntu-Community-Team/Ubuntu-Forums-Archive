---
title: "Strange mouse behaviour"
date: 2009-12-13
forum: General Help
---

### Post by duke_peter on 2009-12-13
Hi all,
I'm new to ubuntu, just installed jaunty 4 days ago (karmic freezes several seconds after startup on my machine), and i have a seemingly strange problem.

Several seconds after the startup my mouse starts behaving in a weird manner: only selected random elements respond to the left click, and right clicking makes context menus of other elements come up (e.g., context menus of panels, of the desktop; only after several, usually 1-2, clicks the proper context menus appear). The keyboard seems a bit sluggish, but otherwise responds properly. No other prblems noticed. The thing that helps is restarting the xorg server.

It's not a deadly problem, but it's very annoying and makes me wonder what is wrong with my configurations. So yeah, once again, rebooting makes no difference, but restarting the xorg server helps. The machine is IBM ThinkPad R40 (which uses the ATI Radeon Mobility 7500 graphics card).

Here is my xorg.conf. I ripped it off from other people out there who use the same hardware =|
```
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dbe"
EndSection

Section "ServerFlags"
	Option 		"DontZap" 	"false" 
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device" 	
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen		0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
	Option          "AccelMethod" "EXA"
	Option		"EXANoComposite" "false"
	Option		"FBTexPercent" "50"
	Option		"MigrationHeuristic" "greedy"
	Option		"DRI" "true"
	Option		"GARTSize"	"64"
	Option		"AGPMode" "4"
	Option		"Colortiling" "On"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	
	SubSection "Display"
			Virtual	1400 1050
	EndSubSection	    

EndSection

Section "DRI"
 Group        "video"
 Mode         0666
EndSection
```

---

