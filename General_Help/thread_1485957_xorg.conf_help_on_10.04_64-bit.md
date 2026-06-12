---
title: "xorg.conf help on 10.04 64-bit"
date: 2010-05-17
forum: General Help
---

### Post by EdwardMorris on 2010-05-17
Hello,

   I've managed to get my USB2VGA monitor to work (partially at least) by using the following xorg.conf. The monitor shows up fine, except like I mentioned in my earlier posts related to this topic, the USB2VGA monitor starts its own X session and I can not move windows back and forth from that screen. The only thing that travels across the screens is the mouse, and I can live with that. The problem I am having now is with the rest of the setup, i.e. I configured the USB monitor to be to the left of the laptop LCD and that worked. I have a second monitor that I configured to show to the right of the laptop LCD and it shows there fine, EXCEPT my laptop LCD and the second monitor (to the right/non USB) form just one huge screen, instead of two individual screens as defined, and I am not using xinerama either. This only happens when I use the USB2VGA adapter. If I unplug the USB2VGA and only use the second monitor, it behaves correctly, i.e it is its own screen, not combined with the main LCD. Could someone please advise on how do I get the USB2VGA to be its own screen (already works), the LCD on the laptop be its own screen and the second monitor to be its own screen. Here is my current xorg.conf

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" LeftOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dbe"
	Load  "record"
	Load  "dri"
	Load  "extmod"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	VertRefresh   50-75
	HorizSync     30-90
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Mobility Radeon HD 3650"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card2"
	Driver      "sisusb"
	VendorName  "SisUSB"
	BoardName   "SisUSB"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport  0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport  0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport  0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport  0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport  0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport  0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card0"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

```

---

### Post by EdwardMorris on 2010-05-19
Any one?

---

