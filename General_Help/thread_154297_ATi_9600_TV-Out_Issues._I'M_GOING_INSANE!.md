---
title: "ATi 9600 TV-Out Issues. I'M GOING INSANE!"
date: 2006-04-02
forum: General Help
---

### Post by Ciddan on 2006-04-02
I've tried everything I can think of to get my TV-out working properly. I've gotten so far as having my TV set as a second monitor (not cloned) and I'm able to set resolutions independantly on the two screens. I CANNOT however for the life of me get the monitor to 50hz - and thus getting color. I've tried modelines, explicit refreshrate settings etc. etc. but I can still only choose to set it to 60hz. The interesting part of my xorg.conf is as follows: (Anything that has been commented out has been tried)

```

Section "Monitor"
	Identifier   "PHILIPS 109B"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 1"
#       HorizSync       30-50
#       VertRefresh     50
#       HorizSync   31.5-90
#       VertRefresh 30-60
	Modeline "800x600_50.00"  31.15  800 824 904 1008  600 601 604 618  -HSync +Vsync
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "TVFormat" "PAL-B"
	Option	    "TVStandard" "VIDEO"
	Option	    "HSync2" "48"
	Option	    "VRefresh2" "50"
	Option	    "UseInternalAGPGART" "off"
	Option	    "KernelModuleParm" "off"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor    "PHILIPS 109B"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 1"
	Device     "ATI Graphics Adapter 1"
	Monitor    "aticonfig Monitor 1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes 	"800x600_50.00"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

What am I doing wrong here? I'd really appreciate any help on the matter.

---

### Post by StalfoS on 2006-04-15
I seem to be having the same problem!  Someone please help!

---

### Post by Ciddan on 2006-04-26
No-one? Please? Anybody?

---

### Post by jabeez on 2006-06-21
Well I got just a little bit further than you it appears, I set up my tv as a second monitor through the display GUI in Kubuntu, and I set the correct resolution for both monitors and I can drag windows between the two screens. In Kubuntu I just set the second monitor to custom/widescreen which had a large range of refresh rates, like 50-150Hz for vert. and hor. I believe, so maybe try that route? I've got color but of course in Linux just when you think you've solved one problem, another rears it's head.....

My problem - no video on the TV, just a black screen where the video should be, and the video that does play on my monitor is pretty jerky and pretty much unplayable in full-screen mode. It looks like I've lost acceleration even though the driver is fglrx in xorg.conf, because GL screensavers are WAY slow. I've been slogging through the forums for days and haven't really found any coherent answers, just a bunch of people's xorg.conf's that I can't make sense of. Any help out there????? Sucks to be so close yet..................We seem to need a dedicated thread for each card or something, because there are a million threads with people trying to figure this out but no good answers.

---

