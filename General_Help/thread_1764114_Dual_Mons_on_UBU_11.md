---
title: "Dual Mons on UBU 11"
date: 2011-05-21
forum: General Help
---

### Post by jfreak53 on 2011-05-21
Ok so I sort of have this working and sort of not ha ha

I have two cards, here is my list:

```
lspci -x | grep VGA
00:09.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```

So since I'm running UBU 11 there was no xorg.conf file.  So I generated one, I removed all but one monitor from the file since it was detecting like 4 or 5.  I started up X with "service gdm start"

It went in fine and one monitor works, the default.  So then I followed the Xinerama guide here on the forum to add a new monitor.  Here is my new xorg.conf file.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
        Option "Xinerama" "true"
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
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
	Load  "record"
	Load  "glx"
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

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:0:9:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "sis"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
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
	Identifier "Screen1"
	Device     "Card1"
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
```

Now here is the deal.  When I startup like this it literally shows two monitors on the task bar in gnome. Also if I run my mouse to the right side of the desktop it keeps going past the screen!  So the desktop is there. The desktop switcher deal shows a huge desktop, but my second monitor (which I know is working because of windows) doesn't come up.

So I tried to go into System -> Preferences -> Monitors.  Won't come up, gives me crap about "RandR extension missing". So I tried to install RandR, it is in the xutil package, I tried to install, hmmm It's already installed.  So I install grandr.

When I try to run grandr it says:

> Xlib:  extension "RANDR" missing on display ":0".                                                                                
Xlib:  extension "RANDR" missing on display ":0".
RandR extension missing

And won't start.  So ok, I went back to terminal alt+ctrl+f1, and service gdm stop.  I edited xorg.conf again and removed the line:

```
Option "Xinerama" "true"
```

Now I started it back up again, service gdm start.  It starts fine, but this time the screen is not expanded at all.  It allows me to get into Monitors and grandr, but no extended screen this time without Xinerama.

So, what did I break ha ha.  I can still use it and the extended desktop is there with Xinerama but the screen won't come on.

Any ideas?

---

### Post by jfreak53 on 2011-05-22
Anyone got any ideas?

---

