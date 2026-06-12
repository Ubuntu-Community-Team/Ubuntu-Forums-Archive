---
title: "XGL Issue...."
date: 2006-06-16
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-16
hey all, I got a really crazy-like error screen, it was all nothing but text, here was the exact error message (without all the crazy jibberish letters around the screen)
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocal Version 11, Revision 0, Release 7.0
Build Operating Syste: Linux 2.6.12 i686
Current Operating System: Linux eclypse 2.6.15-23-386 #1 PREEMPT Tue
May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
         Before reporting problems, check http://wiki.x.org
         to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
               (++) from command line, (!!) notice, (II) informational,
                 (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
  (==) Log file: "/var/log/Xorg.94.log", Time: Fri Jun 16 19:28:26 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) xf86OpenSerial: Cannot open device /dev/wakom
                  No such file or directory.
EError opening /dev/wacom : Invalid arguement
(EE) xf86OpenSerial: Cannot open device /dev/wakom
                  No such file or directory.
EError opening /dev/wacom : Invalid arguement
(EE) xf86OpenSerial: Cannot open device /dev/wakom
                  No such file or directory.
EError opening /dev/wacom : Invalid arguement
(EE) xf86OpenSerial: Cannot open device /dev/wakom
                  No such file or directory.
EError opening /dev/wacom : Invalid arguement
(EE) xf86OpenSerial: Cannot open device /dev/wakom
                  No such file or directory.
EError opening /dev/wacom : Invalid arguement
Synaptics DeviceInit called
SynapticsCrtl called.
Synaptics DeviceOn called
Synaptics DeviceOff called

```
then I hit <Ok>


Would you like to view the detailed X server output as well?
omg... if you guys REALLY need it I'll typ that up to lol.


then after that it says...

The X server is now disabled.  Restart GDM when it is configured correctly

<Ok>

then I have a text base logon screen, I log on, now I have a terminal prompt (no it doesn't have a gui, its entirely black screen white text.

can you guys help me out here? I'de rather not have typed out all that stuff for nothing.

thanks

---

### Post by 23meg on 2006-06-16
Please post your /etc/X11/xorg.conf file.

---

### Post by Patrick-Ruff on 2006-06-16
how? exactly...I can't exactly get on the internet or to a GUI for that matter on this comp...

---

### Post by Patrick-Ruff on 2006-06-16
appologies, I didn't expect 'startx' to work, anyways heres my xorg.conf

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
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
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
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by 23meg on 2006-06-16
If that's because of this failure, open your xorg.conf file with ```
sudo nano /etc/X11/xorg.conf
``` and replace the driver in the "Device" section with "vesa" so that it will look something like this:```
Section "Device"
	Identifier	"blablablablablabla"
	Driver		"**vesa**"
	BusID		"PCI:1:0:0"
EndSection
```Then type ```
startx
```and you'll get back to your desktop environment.

---

### Post by 23meg on 2006-06-16
Try commenting out all the wacom entries (put **#** to the start of each line)

Besides, is fglrx correctly installed?

---

### Post by Patrick-Ruff on 2006-06-16
I don't know what you mean by that wacom thing, but yes fglrx is installed.

---

### Post by 23meg on 2006-06-16
Make this section```
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
```look like this```
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
```

---

### Post by Patrick-Ruff on 2006-06-16
k, I'll try that now.

---

### Post by Patrick-Ruff on 2006-06-16
can anyone help me with using Vi? lol, nano doesn't seem to be available, I can't type text in this bloody thing!!! argh, its frustrating...

---

### Post by 23meg on 2006-06-16
Weird; what error do you get when you try to run nano? Try installing it if it's missing```
sudo apt-get install nano
```or try pico.

---

### Post by Patrick-Ruff on 2006-06-16
ok after finally getting nano to work...... I have a new error now.  its now saying 
```

Fatal server error:
no screens found

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining.

```

---

### Post by 23meg on 2006-06-16
Perhaps something is misconfigured in your /etc/gdm/gdm.conf-custom file. Post it.

---

### Post by Patrick-Ruff on 2006-06-16
I cna't really start x right now.... its all screwed up since it says no screens detected.

```

 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl 

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer flexible=true

```

---

### Post by Patrick-Ruff on 2006-06-16
*yawns* ideas? I followed the directions on the on one of the main threads for getting xgl/compiz working. so I would think that everything in that file is correct.

---

### Post by 23meg on 2006-06-17
Try "0=Xgl" instead of "1=Xgl".

---

### Post by Patrick-Ruff on 2006-06-17
k, testing now

---

### Post by Patrick-Ruff on 2006-06-17
no dice, still says 'no screens found'

---

### Post by Patrick-Ruff on 2006-06-17
nobody care anymore?

---

### Post by jdusablon on 2006-06-17
No, I care, but I don't know how to help you beyond what 23meg said.

I will point out that the wacom stuff seems to be causing some trouble. What is your hardware, anyway? Also, which guide did you follow?

You often have to read several howtos to get something like xgl/compiz working. Also, there are some limitations to ATI card models...they don't all work the same way. There's a well-known bug (and fix) for ATI PCI-E cards, others just can't do XGL (but they'll do AIGLX!)

---

### Post by Patrick-Ruff on 2006-06-17
this is a pcie card. heres my exact system specs

1.6GHz Pentium M
512MB PC3200 DDR2 Ram
64MB ATI Mobility Radeon X300 PCI-E dedicated onboard memory. 

thanks to those that attempt to help.

---

### Post by Patrick-Ruff on 2006-06-17
I'll look at this thread again in like 12 hours, hopefully there'll be useful replys by then


good night everyone.

---

### Post by Patrick-Ruff on 2006-06-17
bump. any ideas whats causing this??? and how to fix it... I want/NEED XGL...

---

### Post by Patrick-Ruff on 2006-06-17
wow, it seems this thread has been forgotten.. 4 pages behind with 0 replys..I call that waiting long enough.... heres a new error I'm getting, I'm still getting the no screens found but its also giving me an error about a command called vt7  and it says unrecognized command... anyone have any ideas? PLEASE don't ignore this thread, its getting very irritating to restart threads over and over.

---

### Post by jdusablon on 2006-06-22
[http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+compiz+thread]("http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+compiz+thread")
and
[http://ubuntuforums.org/showthread.php?t=150854]("http://ubuntuforums.org/showthread.php?t=150854")

These may help. Thee second deals with hardlocking with x700 cards, but it apparently applies to many ATI PCI-E cards.

Good luck!

---

