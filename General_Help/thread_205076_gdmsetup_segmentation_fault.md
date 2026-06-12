---
title: "gdmsetup segmentation fault"
date: 2006-06-27
forum: General Help
---

### Post by xfceslacker on 2006-06-27
When I try to run gdmsetup from the System->Administration->Login Window menu. It just flashes on the screen for a second and crashes. Here is what it does if I try to execute it from the terminal.
```
matthew@Ubuntu:~$ sudo gdmsetup
(gdmsetup:6671): gnome-vfs-modules-WARNING **: Could not initialize inotify

Segmentation fault

```

Here's my gdm log:
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux Ubuntu 2.6.17-rc4 #2 PREEMPT Sun May 21 10:30:05 CDT 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 26 08:45:16 2006
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
AUDIT: Mon Jun 26 08:45:19 2006: 11499 X: client 1 rejected from local host
AUDIT: Mon Jun 26 08:45:19 2006: 11499 X: client 2 rejected from local host
AUDIT: Mon Jun 26 08:45:20 2006: 11499 X: client 1 rejected from local host
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
AUDIT: Tue Jun 27 15:42:00 2006: 11499 X: client 1 rejected from local host
AUDIT: Tue Jun 27 15:42:00 2006: 11499 X: client 3 rejected from local host
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
AUDIT: Tue Jun 27 21:21:50 2006: 11499 X: client 1 rejected from local host

```
And then of course when it says segmentation fault it crashes. I just updated the system(except for kernel upgrades). I'm not using any custom gdm themes or anything. Anyone know what's wrong with this? This is getting on all my nerves. :-|

---

### Post by zxee on 2006-06-27
It looks like there a problem with the xorg.conf file. If you feel confident enough you can open that file with an editor and wade through it. 
This > (EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory. Looks to be the offending party. 
Perhaps commenting out wacom will get your video back, or you can type 
sudo dpkg-reconfigure xserver-xorg and go through the configuration script. That will backup your old non-working xorg.conf and create a new one based on the responses you provide.

---

### Post by xfceslacker on 2006-06-28
I took out everything that had to do with /dev/wacom and it still doesn't work. Here's my current xorg.conf file.

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"i2c"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"15 COLOR"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"15 COLOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	#InputDevice     "stylus" "SendCoreEvents"
	#InputDevice     "cursor" "SendCoreEvents"
	#InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I'm still getting a segmentation fault when running gdmsetup.

---

### Post by zxee on 2006-06-28
Did you try to run the dpkg-reconfigure command as listed in your xorg.conf?

---

### Post by xfceslacker on 2006-06-29
No. I didn't but xorg.conf wasn't the problem. The gdm.conf-custom file was the problem. When you install XGL and then disable it by removing the gdm.conf-custom file it breaks gdmsetup. So I just had to put a gdm-custom.conf file in /etc/gdm. Thanks for trying to help. :)

---

### Post by tseliot on 2006-06-29
Post the output of this command:
```
dmesg | grep NVIDIA
```

and tell me what happens if you type:
```
glxgears
```

---

### Post by xfceslacker on 2006-06-29
As I said in the above post. It was not a problem with X, or my nvidia card. It was a problem with gdm.conf files. It is now fixed. Thanks for trying to help.

---

### Post by Chaoticwhizz on 2006-07-01
Hey I had this same problem. I tried to use compiz and XGL. I missed somethign somewhere and my GDM wouldnt start. Still a Linux newb, I was stuck with the CLI. I reinstalled my original nvidia drivers, ran the reconfigre xorg package like someone suggested earlier but still no luck. Anyway, reading this post gave me the idea of setting my /etc/gdm/gdm.conf-custom file back to it's original. Reboot, then everything is okay again. Just wanted to say thanks.

---

### Post by sanketmedhi on 2006-07-07
Hello, I am facing this same problem. I had installed XGL+Compiz earlier. After I removed it, this problem started appearing. Its been a long time gdmsetup is crashing. From the replies here, I cannot make out the solution. Please elaborate in a few steps how to solve this problem.

---

### Post by snellgrove on 2006-07-07
I deleted all the 'Wacom' garbage in my X11/Xorg.conf file

I have no idea how it got there, theres certainly no graphics tablet attached to my PC. never has been

but anyways, when I deleted it it killed X - the solution?

AT THE BOTTOM, I mean real close to the end of the xorg file, theres this area that looks like this:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

it'll have 3 more lines than what is shown there, about Wacom / Stylus / Eraser or something?

comment them out and see if X starts (type in: 
```

sudo /etc/init.d/gdm restart
```)

if it does, you can delete those 3 lines.

worked a treat here, no Wacom crap and X works :)

---

