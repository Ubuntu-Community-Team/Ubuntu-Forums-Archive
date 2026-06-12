---
title: "some Twinview questions"
date: 2005-02-27
forum: General Help
---

### Post by Beire on 2005-02-27
Ok i got my monitor and Tv Setup as i want it to be. Just a few things aren't working too good.

1. My TV is only showing in Black&White, in windows it show up in colors!
2. Is there a way to increase the flicker filter ? also in windows there is an option to increase this so the tv doesn't flicker. Without it it's quite irritating.


my XFree86 config file:

```
Section "ServerLayout"
	Identifier         "XFree86 Configured"
	Screen       0  "Screen0" 0 0
	InputDevice    "Generic Keyboard" "CoreKeyboard"
        InputDevice    "USB Mouse" "CorePointer"
EndSection

Section "ServerFlags"
	Option	"AllowMouseOpenFail"  "true"
	
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
	FontPath     "/usr/X11R6/lib/X11/fonts/PEX"
	FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/ttf/western"
	FontPath     "/usr/share/fonts/ttf/decoratives"
	FontPath     "/usr/share/fonts/truetype"
	FontPath     "/usr/share/fonts/truetype/openoffice"
	FontPath     "/usr/share/fonts/truetype/ttf-bitstream-vera"
	FontPath     "/usr/share/fonts/latex-ttf-fonts"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load  "ddc"  
	Load  "GLcore"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
        Load  "bitmap" 
	Load  "speedo"
	Load  "type1"
	Load  "freetype"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver      		"keyboard"
        Option		"CoreKeyboard"
	Option       	"XkbRules" 		"xfree86"
	Option 		"XkbModel" 		"pc105"
	Option 		"XkbLayout" 		"be"
EndSection

Section "InputDevice"
        Identifier      	"USB Mouse"
        Driver         	"mouse"
        Option          	"Device"                "/dev/input/mice"
	Option		"SendCoreEvents"	"true"
        Option          	"Protocol"              "IMPS/2"
        Option          	"ZAxisMapping"          "4 5"
        Option          	"Buttons"               "5"
EndSection

Section "Monitor"
	Identifier		"Medion MD1772"
	Option		"DPMS"		"true"
	HorizSync    	30 - 92
	VertRefresh  	40.0 - 70
EndSection

Section "Device"
	Identifier  		"GF6800GT"
	Driver      		"nvidia"
	VendorName  	"Aopen"
	BoardName   	"NVIDIA GeForce 6800GT"
	BusID       		"PCI:1:0:0"
        Option         	"RenderAccel"           			"true"
        Option         	"NvAGP"                 			"1"
        Option      		"RenderAccel"           			"true"
	Option		"TwinView"
	Option		"SecondMonitorHorizSync"		"30-50"
	Option		"SecondMonitorVertRefresh"	"60"
	Option		"MetaModes"				"1280x1024,NULL;NULL,640x480"
	Option 		"TwinViewOrientation" 		"Clone"
	Option 		"TVOutFormat" 				"composite"
	Option		"TVStandard" 				"PAL-B"
EndSection

Section "Screen"
	Identifier 		"Screen0"
	Device     		"GF6800GT"
	Monitor    		"Medion MD1772"
	DefaultColorDepth 24
		SubSection 	"Display"
		Depth     		24
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection
```

---

