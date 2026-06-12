---
title: "Display Settings in Xubuntu"
date: 2006-06-09
forum: General Help
---

### Post by Muzzled on 2006-06-09
Hey there,

I have installed nvidia drivers using tseliot's [scripts]("http://www.ubuntuforums.org/showthread.php?t=139264&highlight=latest+nvidia+drivers"). This installe went pretty well, but it messed up my xorg.conf, so I used the backup one then ran ```
I ran sudo dpkg-reconfigure xserver-xorg
``` to configure xorg.

But I am a little confused here, does xorg.conf have any effect on xfce?
The problem is that I still have the default 800x600(and no 1024x768 available) display settings when I go to the very primitive Settings/Display Settings even though my xorg.conf looks has follow:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"ca"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"FLATRON EZ T710BH"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Monitor		"FLATRON EZ T710BH"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
         Option  "Composite" "Enable"
EndSection 
```

I hope I made it clear enough... feel free to point anything wrong in that.

Thank you!

---

### Post by MetalMusicAddict on 2006-06-09
From this:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"**nv**"
	BusID		"PCI:1:0:0"
	VideoRam	128000
EndSection
```
It looks like you forgot/didnt set the video driver to "nvidia" when you reconfigured. "nv" is the open driver.

---

### Post by Muzzled on 2006-06-09
Thanks for pointing out as I thought nv meant nvidia. :-# 

The problem is bigger than I thought, X won't load anymore if I use nvidia, it gives me something in the line of ```
Failed to load module "glx" ...
Failed to load module "nvidia" ...
Drivers are not available .. 
```

Then running nvidia-settings gives me:
```
ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
```

Yep, I'm a bit confused about getting nvidia drivers to work on Xubuntu. Anyway that's a whole new different thing...

Thanks again for your quick reply.

---

### Post by Muzzled on 2006-06-10
Fixed everything by following what codejunkie said right [here]("http://www.ubuntuforums.org/showthread.php?t=178569&highlight=xfce+nvidia").

Thanks.

---

