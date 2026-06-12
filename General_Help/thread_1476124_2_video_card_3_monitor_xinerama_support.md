---
title: "2 video card 3 monitor xinerama support"
date: 2010-05-07
forum: General Help
---

### Post by dave on 2010-05-07
Hi all,

I have in my machine 2 video cards

1) 01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

2) 04:02.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


The nVidia card has 2 DVI heads, and the ATI has 1 DVI head.  Currently I have them setup in a triple screen environment with the following xorg.conf, where the nVidia card, and the ATI card are on different XScreens, so that windows can't be dragged between them.

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" LeftOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	#Option         "Xinerama" "true"
EndSection

Section "ServerFlags"
	Option         "RandR" "on"
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
	Load  "dri2"
	Load  "dri"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "xrandr"
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
	Driver      "nouveau"
	VendorName  "nVidia Corporation"
	BoardName   "NV44A [GeForce 6200]"
	BusID       "PCI:4:2:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV610 video device [Radeon HD 2400 PRO]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultDepth 24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

```

How do I properly enable Xinerama so that there are 3 monitors, sharing the same XScreen?  Before you say simply, un-comment the Option "Xinerama" line; when doing that the 2 monitors attached to the nVidia card enter mirrored mode, and the ATI monitor is fine.

So the question is, how would I go about having 3 independent monitors sharing the same XScreen?  I've been playing around with this xorg.conf for the past 2 days to no avail.  Any help would be greatly appreciated!!

Thanks
--
Dave

---

### Post by dave on 2010-05-07
I've been reading other posts, and have gotten xinerama working across all three.  Though not yet solved.

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "true"
    Option         "Clone" "false"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "true"
    Option         "Clone" "false"
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
    Load  "dri2"
    Load  "dri"
    Load  "record"
    Load  "extmod"
    Load  "dbe"
    Load  "xrandr"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option      "Protocol" "auto"
    Option      "Device" "/dev/input/mice"
    Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option       "Position" "0 0"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option       "RightOf" "Monitor0"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option       "RightOf" "Monitor1"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV610 video device [Radeon HD 2400 PRO]"
    Option      "monitor-DVI-1" "Monitor0"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "nouveau"
    VendorName  "nVidia Corporation"
    BoardName   "NV44A [GeForce 6200]"
    BusID       "PCI:4:2:0"
    Option      "monitor-DVI-I-1" "Monitor1"
    Option      "monitor-VGA-1" "Monitor2"
    Screen      0
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    DefaultDepth 24
    SubSection "Display"
        Depth     24
        Modes     "1280x1024"
        Virtual   1280 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    DefaultDepth 24
    SubSection "Display"
        Depth     24
        Modes     "1280x1024"
        Virtual   2560 1024
    EndSubSection
EndSection

```

The setup is Monitor0 (ATI card), is the left-most screen.  Monitor1 (nVidia DVI) is the middle.  And Monitor2 (nVidia VGA) is the right-most screen.

Something weird is happening to Monitor1, and subsequently Monitor2.  When the mouse should be moving across the border between monitor1 and monitor2, monitor1 scrolls right, into monitor 2's viewable space.  By the time my mouse is at the right most of monitor2, it seems as if monitor1 and monitor2 are mirrored.

Ideas?  Suggestions?  Thanks!!

--
Dave

---

### Post by dave on 2010-05-11
So after hours upon hours of trying to look into the 'nouveau' driver, it seems as if I can't get it to work at all.  Just stuck with either, mirrored screens, or the left-most monitor scrolls around.

I, with no other options, turned to the nvidia driver and got a "working" configuration.

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      1  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "1"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load "bitmap"
    Load "dbe"
    Load "ddc"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "extmod"
    Load "freetype"
    Load "glx"
    Load "int10"
    Load "type1"
    Load "vbe"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E198FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "radeon"
    VendorName     "ATI Technologies Inc"
    BoardName      "RV610 video device [Radeon HD 2400 PRO]"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    Option        "RenderAccel" "true"
    Option        "AllowGLXWithComposite" "true"
    BusID          "PCI:4:2:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    Option        "RenderAccel" "true"
    Option        "AllowGLXWithComposite" "true"
    BusID          "PCI:4:2:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection 

```

However, now I got another question.  Does anyone know how to get both the nvidia driver, and whatever the proprietary driver for ATI cards (fglrx) to play nice using compositing, and desktop effects?  I remember reading somewhere that with the nvidia driver you don't want to add GLCore.  Any tips, or ideas how to get the drivers to work better?

thx

---

### Post by Mortuis on 2010-05-24
You've shattered my dreams of having a sane 3 monitor solution with Ubuntu.  Currently the best I can do is have two separate X sessions, with two of the screens behaving as one large screen, which is infuriating whenever I maximize a window.  I wish I could get them to all be independent screens within the same x session.

---

### Post by slamhound on 2010-05-24
If you just need windows to maximize to one monitor (rather than both), you can deselect "detect outputs" in CompizConfig Settings Manager General Settings and plug in the values for your monitors on that X-screen (see here: [http://ubuntuforums.org/showpost.php?p=8266363&postcount=1](http://ubuntuforums.org/showpost.php?p=8266363&postcount=1) ). Then this should allow them to maximize correctly. I did this in 9.10, but using two video cards led to a lot of problems for me, so I eventually gave up (some of the problems were discussed in that thread).  I followed some threads on this and never saw any solution that allowed for two cards and effects.  I think the only options were either separate screens that didn't allow dragging windows across screens (but with compiz working) or being able to drag windows across screens but no compiz.  But maybe there is a solution, or maybe things have changed with 10.04.

---

### Post by idallen on 2010-06-05
> **dave said:**
> Something weird is happening to Monitor1, and subsequently Monitor2.  When the mouse should be moving across the border between monitor1 and monitor2, monitor1 scrolls right, into monitor 2's viewable space.  By the time my mouse is at the right most of monitor2, it seems as if monitor1 and monitor2 are mirrored.--Dave

I have the same problem under 10.4 using Xinerama with two monitors
(Left,Middle) on an ATI card (FireMV 2250 with "radeon" driver) and the
third monitor (Right) on an nVidia card (G86 GeForce 8300 GS with "nv"
driver or "nvidia" driver).  I did not have this problem under 9.10.

With Xinerama turned off, the mouse moves perfectly between all three
monitors - the two monitors on the ATI card (Left,Middle) and the single
monitor on the nVidia card (Right).  Unfortunately, it splits my desktop
into two DISPLAYs (ATI and nVidia) and so I can't move windows between
the two.

Under 10.4, with Xinerama on, Left and Middle start out showing the
same content.  (This looks like mirror mode, but isn't.)  Starting on
Left, I can move the mouse to the right, and it crosses both Left and
Middle simultaneously until it reaches the right side of both.  Then,
we discover that Middle is actually a scrolling double-width screen with
only a single width showing - as I move against the right edge of Middle,
the mouse causes Middle to scroll, until both virtual Middle screens have
been crossed, then Middle stops scrolling and the mouse moves to Right.

At this point, with the mouse all the way to the right, I have three
monitors showing three different parts of the full Xinerama desktop.

Moving the mouse back toward the left from the Right monitor, the mouse
crosses Right, leaves Right into Middle, them when the mouse hits the
left side of Middle, the mouse also appears on the right side of Left,
and as I move the mouse left, Middle scrolls until it is showing exactly
the same content as Left.

I need to find out how to tell Middle not to scroll and to show only
the right side of its double-size viewport.

This didn't happen under 9.10.  It's new in 10.4

---

### Post by etothepii on 2010-07-06
I am having the exact same problem and it is driving me mad, I have now been faffing with this for over a month having wasted an enormous amount of time.

Does anyone have any ideas? The fact that I can get the damn computer to produce 4 screens and display them all at the same time with Xinemara suggests that everything is almost there it is just that on one of my monitors it insists on moving when I move the mouse.

I actually have 4 monitors, with 2 attached to each of two cards.

Any thoughts anyone.

---

### Post by idallen on 2010-07-08
The new "ZaphodHeads" option fixes this problem.
See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/591104]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/591104")
Here is a working xorg.conf for three monitors:

```
Section "ServerLayout"
	Identifier   "Ian"
	Screen       "Screen Left" 0 0
	Screen       "Screen Middle"  RightOf "Screen Left"
	Screen       "Screen Right"  RightOf "Screen Middle"
	Option       "Xinerama"
EndSection

Section "Screen"
	Identifier "Screen Left"
	Device     "Device Left"
	# this isn't absolutely necessary but it helps window placement
	SubSection "Display"
		Virtual 1600 1200
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen Middle"
	Device     "Device Middle"
	# this isn't absolutely necessary but it helps window placement
	SubSection "Display"
		Virtual 1600 1200
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen Right"
	Device     "Device Right"
	# this isn't absolutely necessary but it helps window placement
	SubSection "Display"
		Virtual 1600 1200
	EndSubSection
EndSection

Section "Device"
	Identifier  "Device Left"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "FireMV 2250"
	BusID       "PCI:4:0:0"
	Option	    "ZaphodHeads" "DVI-0"
	Screen	    0
	#Option      "Monitor-DVI-0" "Left Monitor"
	#Option      "Monitor-DVI-1" "Middle Monitor"
EndSection

Section "Device"
	Identifier  "Device Middle"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "FireMV 2250"
	BusID       "PCI:4:0:0"
	Option	    "ZaphodHeads" "DVI-1"
	Screen	    1
EndSection

Section "Device"
	Identifier  "Device Right"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "G86 [GeForce 8300 GS]"
	BusID       "PCI:5:0:0"
	Screen	    0
	#Option      "Monitor-DVI0" "Monitor Right"
EndSection


```

---

### Post by Despot on 2010-07-25
I have not been able to get this ZaphodHeads setting to work with the nouveau driver--the X log says the option is ignored. Anyone have an alternative that works with nouveau?

[edit] The alternative that worked for me was to get the nvidia driver working: see [http://ubuntuforums.org/showthread.php?p=9644558](http://ubuntuforums.org/showthread.php?p=9644558) Would've liked to use the open-source driver, but it doesn't seem stable enough...

---

