---
title: "1280x800 nomore after ATI-driver install.."
date: 2006-03-02
forum: General Help
---

### Post by Foxcat on 2006-03-02
Hi.
I have an Acer Travelmate 4501 which works perfekt with Ubuntu. But because the performance was so-so, I decided to install the 686-smp kernel and the ATI-driver. Everything went fine (thanks to all the information I found here on the forums!) and the framrate in one of the screen savers (Atlantis) went up from 4 to 40 fps. Great!
BUT, I cannot choose 1280x800 as resolution nomore. I'm stuck with 1024x768 and that's no good on my widescreen laptop.
I've tried to configure the xorg file by both running the setup program (forgot what it's called) and to manually edit it. But the resolution is stuck to 1024x768 no matter what I enter in the xorg file. I believe to think that the ATI driver is not ment to run on an laptop, that there is one specific to laptops.
Please help a Linuxbeginner who really want to get rid of Windows! :???:

---

### Post by florizs on 2006-03-02
I have a Fujitsui-siemens laptop with wideScreen and 1200x800 resolution and I had the same problems.
I downloaded the ati driver from the ATI.com website and installed.
after running fglrxconfig I had a 1024x786 resolution again, however this time it changed when I modified xorg.conf to 1200x800 resolution.
i'm at work now but if you want I can post my xorg.conf file later

---

### Post by Foxcat on 2006-03-02
Thanks! That would be great!! :-D

---

### Post by Foxcat on 2006-03-06
I still havent solved my problem with the resolution. So I post my xorg-file here and hope that someone tells me what to do. ;) 

---------------------------------------------------------------

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbLayout"	"se"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9700"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-82
	VertRefresh	50-85
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9700"
	Monitor		"Generic Monitor"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1280x800" "1200x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

