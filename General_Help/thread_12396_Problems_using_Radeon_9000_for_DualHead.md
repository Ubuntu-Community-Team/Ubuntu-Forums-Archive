---
title: "Problems using Radeon 9000 for DualHead"
date: 2005-01-24
forum: General Help
---

### Post by lemming on 2005-01-24
Hi!

I've tried to get my Radeon 9000 working as DualHead. I think the XFree86Config-4 is ok. But i only get a mirror of my default screen (aka Screen 1 in the Config). 

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
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Identifier	"ATI 9000 Output2"
	Driver		"ati"
	BusID		"PCI:1:0:1"
EndSection

Section "Device"
	Identifier	"ATI 9000 Output1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC V921"
	HorizSync	31-96
	VertRefresh	55-160
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Belinea 10559"
	HorizSync	28-50
	VertRefresh	43-75
	Option 		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Device		"ATI 9000 Output1"
	Monitor		"NEC V921"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"Screen 2"
	Device		"ATI 9000 Output2"
	Monitor		"Belinea 10559"
	DefaultDepth	15
	SubSection	"Display"
		Depth	15
		Modes	"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DualHead"
	Screen		"Screen 1" RightOf "Screen 2"
	Option		"Xinerama" "On"
	Option 		"Clone" "Off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
	
Section "DRI"
	Mode	0666
EndSection

``` 

The XFree86.0.log reports only this Warning:

```
.
.
.
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI 9000 Output1".
(II) ATI:  Candidate "Device" section "ATI 9000 Output2".
(WW) ATI:  PCI/AGP Mach64 in slot 1:0:1 could not be detected!
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
.
.
.
``` 

But lspci says the PCI-Adress is correct!?

```
.
.
.
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
.
.
.
``` 

I have tried to setup the Secondary Display Controller as my default screen.

```
Section "ServerLayout"
	Identifier	"DualHead"
	#Screen		"Screen 1" RightOf "Screen 2"
	Screen		"Screen 2"
	Option		"Xinerama" "On"
	Option 		"Clone" "Off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
``` 

The result is, GDM isn't starting. 

That is what XFree86.0.log is telling me (nothing):
```
.
.
.
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI 9000 Output2".
(WW) ATI:  PCI/AGP Mach64 in slot 1:0:1 could not be detected!
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found
.
.
.
```

Thanks for help!

---

### Post by lemming on 2005-01-27
*pushing* :)

---

