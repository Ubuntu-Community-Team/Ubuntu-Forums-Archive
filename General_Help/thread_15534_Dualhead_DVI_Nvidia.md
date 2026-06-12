---
title: "Dualhead DVI Nvidia"
date: 2005-02-15
forum: General Help
---

### Post by shrike on 2005-02-15
Hi,

I have a problem getting the following to work together correctly. ](*,) 

Asus Nvidia Geforce 4200 Dual DVI + Two Dell 1901FP displays

My problem pertains to the fact that no matter how I customize the XF86Config-4 file I can't seem to get dual display up and working.  I would post my current config file, but at this juncture I believe better guidance might be had by seeing someone else's config file and duplicating it.  

I have tried eveything on the forums but no matter what I do it just loads up on one monitor.

Please help!

---

### Post by shrike on 2005-02-19
\\:D/ 

Hello,

Update on my progress...

I recently found an update as how to do this propperly seems that I don't need to specify a few things that were preventing me from even having one screen in X windows posting propperly.  Specifically I was having trouble with the refresh rate and resolution... escentially I found that the nvidia driver seems to do a lot of this detection during the boot process.?....

in any case this is my config if it helps anyone else....

//***

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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Resolution"		"100"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	VendorName	"Dell"
	ModelName	"1901FP"
	HorizSync	30-80
	VertRefresh	56-76
	Option		"DPMS"
	#UseModes	"Modes[0]"
EndSection

Section "Monitor"
	Identifier	"Monitor[1]"
	VendorName	"Dell"
	ModelName	"1901FP"
	HorizSync	30-80
	VertRefresh	56-76
	Option		"DPMS"
	#UseModes	"Modes[1]"
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024""1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Device		"Device[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024""1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "Device"
	BoardName	"Geforce4"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Identifier	"Device[0]"
	Screen		0
	Option		"Rotate" 	"off"
	Option		"NoLogo"
	Option		"RenderAccel"	"true"
	Option		"NvAGP"		"2"
	VendorName	"NVidia"
EndSection

Section "Device"
	BoardName	"Geforce4"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Identifier	"Device[1]"
	Screen		1
	Option		"Rotate" 	"off"
	Option		"NoLogo"
	Option		"RenderAccel"	"true"
	Option		"NvAGP"		"2"
	VendorName	"NVidia"
EndSection

Section "ServerLayout"
	Identifier	"Layout[all]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Clone"		   "off"
	Option		"Xinerama"	   "off"
	Screen		"Screen[0]"
	Screen		"Screen[1]" LeftOf "Screen[0]"
EndSection

Section "DRI"
	Mode	0666
EndSection

//****

The only problem that I'm having currently is that I can't seem to drag windows across from my main monitor[0] over to the left monitor[1]. other then that I'm happy as can be now that I"ve got it working because my productivity is that much more with two sweet FP's going...

---

### Post by valadil on 2005-02-20
I notice that your config file doesn't go into too much depth about varying resolutions.  I don't know that changing them will help with your dragging problem at all, but its something to poke at.  Here are the relevant bits from my xorg.conf:

Section "Device"
	Identifier	"NVIDIA Corporation NV10DDR [GeForce 256 DDR]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"	"true"
	Option		"nologo"	"true"
	Option		"NvAGP"		"3"
	Option		"ConnectedMonitor"	"CRT,CRT"
	Option		"MetaModes"	"1280x960,1280x960 ; 1280x960,NULL ; NULL,1280x960 ; 1024x768,1024x768 ; 1024x768,NULL ; NULL,1024x768 ; 800x600,800x600 ; 800x600,NULL ; NULL,800x600 "
	Option		"SecondMonitorHorizSync"	"30-70"
	Option		"SecondMonitorVertRefresh"	"50-120"
	Option		"TwinView"
	Option		"TwinViewOrientation"	"RightOf"
	Option		"AllowGLXWithComposite"	"true"
EndSection

---

### Post by AndresBarcenas on 2005-02-25
Hello Shrike,
I have the same Video Card Model and I have been able to get the dual screens working  with the latest version of Xorg and XFree86. It seems as though the nvidia driver works perfectly fine on XFree86, but not on Xorg. I had to use the driver version 6111 on Xorg to get the dualhead working.

Here are a couple of things you can try :
1. Download different nvidia driver versions
2. Try to get the second monitor to come up without any specials options such as composite, glx, etc...

Here is my config for the second monitor :

Section "Device"
    Identifier  "NVIDIA"
    Driver      "nvidia"
    VideoRam 131072
    Option "NvAGP" "1"
    Option "TwinView" "true"
    Option "SecondMonitorHorizSync" "30.0-70.0"
    Option "SecondMonitorVertRefresh" "50.0-160.0"
    Option "MetaModes" "1280x1024, 1280x1024; 1280x1024, 1280x1024;"
    Option "TwinViewOrientation" "LeftOf"
EndSection

Even though you use xinerama off, it will still use it..

Regarding the ServerLayout, I think the nvidia driver will not use it... Here is my :

Section "ServerLayout"
        Identifier     "XFree86 Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
#       Option      "Xinerama" "off"
EndSection

As you can see, I did not specify any screens, the nvidia driver will take care of that for you.

Let me know, if this helps.

---

### Post by c_dog on 2005-02-26
Check out my reply to Sascha here:  [http://ubuntuforums.org/showthread.php?t=16523](http://ubuntuforums.org/showthread.php?t=16523)

In short, you can only drag windows across a single "Twinview" desktop Screen that spans two monitors, not between two seperate X-Screens. Twinview treats both monitors like one big X-Screen.

c_dog

---

### Post by shrike on 2005-02-27
thank you all very much for responding to my post  :lol: !

I'm working the next couple of days so I'll have to try to wait until monday to update and tell you if that fixed my problem or not.  Just thought that I would pop on and say thank you for the help ... and all of you are demonstrating why this is such a great distro/forum! :)  thanx for helping a newbie out.

---

### Post by cmsj on 2005-03-01
I have written up some very quick and basic notes on getting twinview working:

[http://www.ubuntulinux.org/wiki/XineramaMultipleMonitors](http://www.ubuntulinux.org/wiki/XineramaMultipleMonitors)

---

