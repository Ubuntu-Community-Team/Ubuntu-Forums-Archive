---
title: "Upgrade broke VIA"
date: 2006-04-30
forum: General Help
---

### Post by petehall on 2006-04-30
I recently managed to get VIA drivers working for my motherboard (a K8MM-V with onboard S3 Graphics UniChrome Pro). Following my usual apt-get update && apt-get upgrade this morning, I now can't boot into X - my monitor (Sony SDM-HS95P) is complaining about an "out of range error". If I switch back to using the vesa driver, it works fine, though obviously I don't get the benefits of the VIA driver.

I can't remember exactly which packages were upgraded this morning, so I can't roll them back to an earlier version. There was some mysql stuff, ruby stuff and firefox stuff, but I definitely remember some other packages, one of which is presumably the culprit. Does apt-get leave a log anywhere?

This is my xorg.conf, which until today worked fine:

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
	#Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SDM-HS95P"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	48-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SDM-HS95P"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Can anybody help me please?

---

### Post by petehall on 2006-04-30
[QUOTE=petehall]Can anybody help me please?[/QUOTE]

No need - figured it out myself. One of the upgraded packages was xserver-xorg-driver-via, which I had previously replaced with the version at [http://www.openchrome.org/snapshots/ubuntu/](http://www.openchrome.org/snapshots/ubuntu/) - to get the via drivers working again, all I had to do was reinstall the version that I downloaded from the above URL.

---

