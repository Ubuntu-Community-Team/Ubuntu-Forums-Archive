---
title: "TV in black-white unless reboot with TV plugged in"
date: 2006-03-05
forum: General Help
---

### Post by guano on 2006-03-05
I din't know if this is a bug or some "feature", but I can only have colors with SVIDEO TV-OUT if I reboot my notebook with the TV plugged in. Just restart the X system doesn't work, it takes a reboot, with the TV plugged.

here's my xorg.conf:

```


Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Option "TVStandard" "PAL-M"
	Option "TVOutFormat" "SVIDEO" # "Composite" or "SVIDEO" or "RBG"
	Option "ConnectedMonitor" "TV" 
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
EndSection


Section "Monitor"
	Identifier "TV"
	HorizSync	30-50
	VertRefresh 60
EndSection

Section "Screen"
	Identifier	"LCD_CRT"
	Device		"LCD_CRT"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD_TV"
	Device		"LCD_TV"
	Monitor		"LCD"
	DefaultDepth	24
	Subsection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "CRT"
	Device "CRT"
	Monitor "CRT"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768"
	EndSubsection
EndSection

Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier "LCDandTV"
	Screen 0 "LCD_TV"
	Screen 1 "TV" RightOf "LCD_TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDandCRT"
	Screen 0 "LCD_CRT"
	Screen 1 "CRT" RightOf "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option "DefaultServerLayout" "LCDandTV"
#	Option "DefaultServerLayout" "LCDandCRT"
EndSection


Section "DRI"
	Mode	0666
EndSection

```

---

