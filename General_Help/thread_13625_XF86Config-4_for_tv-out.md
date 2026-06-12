---
title: "XF86Config-4 for tv-out"
date: 2005-02-01
forum: General Help
---

### Post by imightbegiant on 2005-02-01
I've looked at a bunch of other posts on this topic, but I havn't come up with a configuration that works for my setup.  I have a crt for my main monitor at 1152x864 and I have a tv that I want to use as a clone for movies at 800x600.  The tv clones during boot up and when I'm at the text-only run level, but that's it. Once gdm starts, only the crt is enabled. Here's my XF86Config-4.

```
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option "TwinView"
#	Option "TwinViewOrientation" "RightOf"
#	Option "MetaModes" "1152x864,800x600"
#	Option "ConnectedMonitor" "crt,tv"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"tv"
	HorizSync	30-50
	VertRefresh	60	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"Generic Monitor"
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
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier		"sTV"
	Device			"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor			"tv"
	DefaultDepth		16
	Option			"ConnectedMonitor" "TV"
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Screen		"sTV" LeftOf "Default Screen"
	Option		"TwinView" "On"
	InputDevice	"Logitech Cordless Desktop Pro" "CoreKeyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

What needs changing so that it works with gnome?

---

### Post by imightbegiant on 2005-02-05
I came across this site

[http://www.sh.nu/nvidia/XF86Config](http://www.sh.nu/nvidia/XF86Config)

which lists a bunch of different cofigurations that helped me out. Now that I have tv out working in clone mode, the only thing i'm having trouble with is the resolution difference between my crt and tv. I have the crt at 1152x864 and the tv at 800x600, but the tv only shows a part of my desktop instead of a shrunken down complete copy like I want. Is there any way to make this work in video playback other than changing the crt's resolution down to the tv's?

---

### Post by Mgcross on 2005-03-23
[QUOTE=imightbegiant]I came across this site

[http://www.sh.nu/nvidia/XF86Config](http://www.sh.nu/nvidia/XF86Config)

which lists a bunch of different cofigurations that helped me out. Now that I have tv out working in clone mode, the only thing i'm having trouble with is the resolution difference between my crt and tv. I have the crt at 1152x864 and the tv at 800x600, but the tv only shows a part of my desktop instead of a shrunken down complete copy like I want. Is there any way to make this work in video playback other than changing the crt's resolution down to the tv's?[/QUOTE]

Yes, try this:

Section "ServerLayout"
Identifier "AGPTwinView"
Screen "ScreenAGPTwinView" 0 0
InputDevice "Configured Mouse" "CorePointer"
InputDevice "Generic Keyboard" "CoreKeyboard"
EndSection

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
EndSection

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is
# received. This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging
#NoTrapSignals
# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.
#DontZap
# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences. This allows clients to receive these key events.
#DontZoom
# This allows the server to start up even if the
# mouse device can't be opened/initialised.
Option "allowmouseopenfail"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
#change "xorg" to "xfree86" if you are using such  	
        Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbOptions"	"multi"

#change your keyboard layout to whatever you like :)


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


#TV FULLSCREEN modes for 768x576 in 50 kHz
#ModeLine "768x576" 50.00 768 832 846 1000 576 590 595 630

# be sure to replace these values with values appropriate for your
# monitor!
Section "Monitor" 
	Identifier	"MyMonitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Device"

# update this with the PCI id of your card. Consult the output
# of the 'lspci' command. The BusID is usually optional when
# only using one graphics card.
# sample twinview setup
Identifier "NV AGP TwinView"
Driver "nvidia"
VendorName "nvidia"
BoardName "GeForce 4 MX 440"
Option "TwinView" "Yes"
#I have added these two lines myself after reading another manual ;)
#without them this damn thing didn't work.
#If you use flat panel you should use: BFP-0 instead of CRT-0 or TV-0
Option "HorizSync" "CRT-0: 30-95, TV-0: 30-50"
Option "VertRefresh" "CRT-0: 50-160, TV-0: 60"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"

#Here you can choose how to manage the twin view display
#Clone means that your TV will show the same display as your CRT monitor
#for other possibilities check the readme file (it comes with the drivers)

Option "TwinViewOrientation" "RightOf"

#If you use SViodeo tvout you should change this option to SVIDEO
#otherwise leave it unchanged

Option "TVOutFormat" "Composite"

#here you select TV standard used in your region
#for example: PAL-G, NTSC-M etc. check the readme for full list

Option "TVStandard" "NTSC-M"

#Here you select meta screen modes for your twinview
#don't ask me what it means, I dont understand it fully, but I know
# that you have to give pairs of screen resolutions. In readme I have found
#that it can be done like this: "1280x1024,1280x1024; 1024x768,1024x768"
#but in practice it didn't work for me :( So I have read more and found out
#that we can specify these settings like here:

Option "MetaModes" "CRT-0: 1024x768, TV-0: 1024x768"

#remember to change CRT or TV to BFG if one of your display is flat panel

Option "ConnectedMonitor" "crt,TV"

EndSection

Section "Screen"
Identifier "ScreenAGPTwinView"
Device "NV AGP TwinView"
Monitor "MyMonitor"
DefaultDepth 24
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x400"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection


MAke note Option "TwinViewOrientation" "RightOf" it will put a second desktop just where it says on the TV. If you use Xine (some like it, some dont) you can move the display window of xine to the tv, make it full screen and use the control window on your monitor...I find it works better for me than cloning the display. Be sure to use your current xorg.config file as a refference for monitor refresh, etc. If you screw something up, have a look at the output that informs you of where the conf script died...will help you fix it quickly. Hope this was of some help....

---

