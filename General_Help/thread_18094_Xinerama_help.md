---
title: "Xinerama help"
date: 2005-03-04
forum: General Help
---

### Post by Leif on 2005-03-04
I've checked previous posts on how to set Xinerama up, but I can't figure this out  8-[ 

I've got two cards and monitors that work fine when used one at a time, but when I try to put them together by enabling the line with the LeftOf, the mouse flickers from one monitor to the other a couple of times and then I get the message that gdm failed. The relevant parts of my XF86Config-4 file are : 

Section "Device"
	Identifier	"S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]"
	Driver		"s3"
	BusID		"PCI:0:5:0"
EndSection

Section "Device"
	Identifier	"Nvidia GeForce 2 MX-200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "NoLogo"
	Option          "RenderAccel"   "true"
	Option          "NvAGP"         "1"
EndSection

Section "Monitor"
	Identifier	"Left Monitor"
	HorizSync	30-65
	VertRefresh	50-75
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Right Monitor"
	HorizSync	30-65
	VertRefresh	50-75
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Left Screen"
	Device		"S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]"
	Monitor		"Left Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
Identifier      "Right Screen"
Device          "Nvidia GeForce 2 MX-200"
Monitor         "Right Monitor"
DefaultDepth    24
SubSection "Display"
Depth           1
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth           4
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth           8
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth           15
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth           16
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth           24
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"Xinerama" "on"
	Option		"Clone" "off"
	Screen		"Right Screen" 
	Screen "Left Screen" LeftOf "Right Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

I have the nvidia drivers installed. In case it matters, the old S3 is the first one to be initialized in the bios, but trying to put Left Screen first and Right Screen RightOf Left Screen gives the same problem. Any ideas ?

---

### Post by Leif on 2005-03-05
Got this sorted out with help from a friend : the depth settings for both devices need to be the same. I've seen other configurations where this wasn't necessary, but at least in this instance it was.

---

