---
title: "Nvidia 5200 Tv-out"
date: 2006-02-04
forum: General Help
---

### Post by Bart123 on 2006-02-04
Hi U all.
Simple request in mind: to watch video files on TV via Nvidia FX5200 tv out.
So far, I'm only getting generic desktop on my tv, no mouse movement or icons or any change at all (except one time the date and time window opened...)...
What am I missing to complete this task? Don't care for dual view or anything, jst run those damn videos on my TV...
Thanks a lot


XORG.CONF

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,il"
	Option		"XkbOptions"	"grp:alt_shift_toggle"
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Screen            0
        Option           "ConnectedMonitor" "Monitor[0]"
        
EndSection

Section "Device"
   Identifier      "Device[1]"
   Driver          "nvidia"
   Screen       1
   Option       "TwinView" "true"
   Option       "TwinViewOrientation" "Clone"
   Option          "TVOutFormat" "S-VIDEO" #or S-VIDEO etc
   Option          "TVStandard" "PAL-G" #or NTSC etc
   Option          "ConnectedMonitor" "TV"
   BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection 

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
	HorizSync	30-64
	VertRefresh	50-100
        Modeline "640x480"     31.5   640  680  720  864   480  488  491  521
        Modeline "800x600"     50     800  856  976 1040   600  637  643  666 +hsync +vsync
        Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
        Modeline "1024x768"    85    1024 1032 1152 1360   768  784  787  823
        Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054

EndSection

Section "Monitor"
   Identifier    "Monitor[1]" #TV
   HorizSync 60
   VertRefresh 30-150
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
	EndSubSection
EndSection

Section "Screen"
   Device "Device[1]"
   Identifier "Screen[1]"
   Monitor "Monitor[1]"
   DefaultDepth 24
        SubSection "Display"
               Depth 24
               Modes "1024x768"
        EndSubSection   
EndSection 

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 "Screen[0]"
        Screen 1 "Screen[1]" LeftOf "Screen[0]" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

