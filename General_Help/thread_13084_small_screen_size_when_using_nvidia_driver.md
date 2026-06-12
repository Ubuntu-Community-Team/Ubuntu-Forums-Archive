---
title: "small screen size when using nvidia driver"
date: 2005-01-28
forum: General Help
---

### Post by BigCdaAnswer3 on 2005-01-28
Hey everyone, I'm still pretty new at Ubuntu and I am very happy I can get 3d support at all for my nvidia card. The thing is, I have a brand new laptop with a GeForce 440 Go Nvidia card for graphics. The standard "nv" driver worked perfectly, but whenever I used apt-get to get the "nvidia" driver and put that in my xorg.conf file, It works, but the screen shows up on the left hand side at about 1024x768 (my screen size is actually 1200x800) and it is filled with black space on the right. I really don't think I'm doing anything wrong in the config file but if someone could just check it out I would appreciate it. I think it's just a problem with the driver. 

I was going to do a screenshot but I don't know how to get my SecureDigital card to work either (but that's something different entirely) So if I can I will post a picture because I don't think I'm the only one having this problem.

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
#	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
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
	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
  Identifier    "Synaptics Touchpad"
  Driver        "synaptics"
  Option        "Device"        "/dev/psaux"
  Option        "Protocol"      "auto-dev"
  Option        "LeftEdge"      "1700"
  Option        "RightEdge"     "5300"
  Option        "TopEdge"       "1700"
  Option        "BottomEdge"    "4200"
  Option        "FingerLow"     "25"
  Option        "FingerHigh"    "30"
  Option        "MaxTapTime"    "180"
  Option        "MaxTapMove"    "220"
  Option        "VertScrollDelta" "100"
  Option        "MinSpeed"      "0.06"
  Option        "MaxSpeed"      "0.12"
  Option        "AccelFactor" "0.0010"
  Option        "SHMConfig"     "on"
#  Option       "Repeater"      "/dev/ps2mouse"
EndSection

#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"NvAGP"			"1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-64
	VertRefresh	43-60
	Option		"DPMS"
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
        Modeline        "1280x800_60.00" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
#		Depth		1
#		Modes		"1280x800"
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		4
#		Modes		"1280x800"
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		8
#		Modes		"1280x800"
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960"
#		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960"
#		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
#		Modes		"1280x800"
		Modes		"1280x960"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

---

### Post by BigCdaAnswer3 on 2005-01-28
I got my friend's digital camera to take a shot of what it actually looks like if this helps. Both images are attached.

---

### Post by Somatik on 2005-01-29
I also got a new hp portable, and can't get the screen working in native resolution, the only choice I have in the resoluton chooser is 640*480. The actual resolution of my display is 1440*900

---

### Post by piedamaro on 2005-01-29
Try various resolutions (it seems from your config file that you have only "1280x960").
Try to launch xvidtune from a terminal.

---

### Post by brainkilla on 2005-01-29
The above post makes sense, enable the desired resolution in the Xconfig, and be sure to enable the same resolution through  System Config > Screen Resolution in the Gnome's Computer menu...

---

### Post by kesla on 2005-02-01
[QUOTE=Somatik]I also got a new hp portable, and can't get the screen working in native resolution, the only choice I have in the resoluton chooser is 640*480. The actual resolution of my display is 1440*900[/QUOTE]
I've got a pretty old Dell Inspiron (8100) with the same problem as you describe.
And when I try to change my screen resolution in gnome, the only availible resolution is 640 * 480.
this problem have never occured for me when dealing with Xfree86 drivers instead of X.org.
I'm a newbie when it comes to linux, so it would be nice if someone could help me with this and explain how to solve the problem with a detailed description... So that I can't do wrong :)
Thanks in advance

---

### Post by mrgenixus on 2005-03-03
check /etc/modprobe.d/nvida for a line that reads:
options nvidia NVreg_Mobile=0
it should be there, though I'm not certain about the value. "0" worked for me.

I have r3000 series r3370us laptop.

---

### Post by BigCdaAnswer3 on 2005-03-03
[QUOTE=mrgenixus]check /etc/modprobe.d/nvida for a line that reads:
options nvidia NVreg_Mobile=0
it should be there, though I'm not certain about the value. "0" worked for me.
[/QUOTE]

The only file I have in /etc/modprobe.d/ that starts with nvidia is nvidia-kernel-nkc.
Upon looking at this file in emacs it only has one line:

alias char-major-195* nvidia

I'm gonna try to create a file in there name nvidia with
options nvidia NVreg Mobile=0 
and see how we do....

---

### Post by BigCdaAnswer3 on 2005-03-03
nope no luck :(

---

### Post by kayali on 2005-03-14
well... the nvidia drivers have the bad habit to trust what your monitor claims to be its native resolution, and as bad things always happen, you monitor is lying, though maybe unintentionaly. As told in the nvidia driver's readme (who reads this anyway?) there's an option to ignore what the monitor says. That is, in your device section, right after telling xorg to use the 'nvidia' driver, you need this :

Option "IgnoreEDID" "true"

then, provided you have a good modeline, you should get the resolution you want.

Hope it helps. (tada, this was my first post... downloading hoary daily as we speak... count me in in a few hours ;)

---

### Post by Somatik on 2005-03-15
problems fixed with the "buntu 5.04 Preview"

---

