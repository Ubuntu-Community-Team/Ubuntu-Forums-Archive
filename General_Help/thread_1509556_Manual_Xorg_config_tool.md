---
title: "Manual Xorg config tool"
date: 2010-06-14
forum: General Help
---

### Post by bakegoodz on 2010-06-14
Xorg has pissed me off for a while. A couple of years ago I used to be able to run dpkg-reconfigure and manually set the settings I needed. Lately it only automaticly Plug-N-Prays all the settings. Which doesn't always work right. I have a couple laptops that don't display the whole screen because I can't choose the resolution I need. 

Is there manual config tool were you can tell Xorg exactly what to do and turn off auto-config crap?

Yes I have tried fidding with xorg.conf, everything I've tried doesn't do anything, it's like Xorg completely ignores the file now.

---

### Post by 67GTA on 2010-06-14
Does running ```
xrandr
``` in a terminal list your correct screen resolution?

---

### Post by skooter1121 on 2010-06-14
I have the same problem. Been quite frustrated trying for a solution.

xrandr - does not give a 1024x768 option. Only 800x600. Even with the proper, (found by OS), older ATI video drivers loaded.

I was able to get it running correctly on one laptop by manually adding the older ATI driver. Verified that it was there through synaptic, then removing all the other xorg servers. Rebooted and the resolution of 1024x768 was now a resolution option.

I suggest this to you only as a possible last-ditch solution, as it might totally screw up everything, so I would only try it on a fresh install.

I did have success with another machine that had Ubuntu 8.4, where I was able to edit the xorg.conf save it and then add it to a 10.4 fresh install. Seems like a lot of work.

Would also like to know if there is a solution to this. It appears that the xorg.conf is no longer required, and even if you are able to correct/edit it, it does nothing. There was a command that would create a xorg.conf file, but that doesn't work also.

Any solution would be helpful.

-Skooter

---

### Post by 67GTA on 2010-06-14
If xrandr doesn't see your res, then a manual xorg is probably the best option. I would also file a bug on launchpad so this can be fixed. Auto detection is awesome when it works. A few configs always fall through the cracks though.

---

### Post by skooter1121 on 2010-06-14
From what I've read this is not a bug. The autodetect does not rely on  Xorg conf anymore, so 10.40 does not even have one. So they are not going to fix it. 

There has to be some other workaround available, there are lots of older laptops that would easily run ubuntu in 1024x768.

-S

---

### Post by 67GTA on 2010-06-14
10.04 will still use xorg.conf if it is present. It just doesn't create one by default.

---

### Post by bakegoodz on 2010-06-16
Is there a way to tell it to use xorg.conf? Because I can't get it to ever follow it.

---

### Post by 67GTA on 2010-06-16
It should be used by default if it is correct. Post a copy of your xorg.conf along with the output of ```
lspci -v
```

---

### Post by bakegoodz on 2010-06-18
Search and tweaked for the longest time, finally fixed it after finding this page [http://ubuntuforums.org/showthread.php?t=763964&page=9](http://ubuntuforums.org/showthread.php?t=763964&page=9)
I copied the Monitor section of someone that got it working with that also had a Trident Cyberblade Video hardware.
Apparently Xorg doesn't work right with many (probally all) Trident Cyberblades, and will probably never will since the laptop I'm using is 8 years old, probably too old for the Xorg devs to care.
This is the xorg.conf that finally worked for me:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "dri2"
	Load  "glx"
	Load  "extmod"
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
	VertRefresh  56-61
	HorizSync    31.5-49
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "PciRetry"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SetMClk"            	# <freq>
        #Option     "MUXThreshold"       	# <i>
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "NoMMIO"             	# [<bool>]
        #Option     "NoPciBurst"         	# [<bool>]
        #Option     "MMIOonly"           	# [<bool>]
        #Option     "CyberShadow"        	# [<bool>]
        #Option     "CyberStretch"       	# [<bool>]
        #Option     "XvHsync"            	# <i>
        #Option     "XvVsync"            	# <i>
        #Option     "XvBskew"            	# <i>
        #Option     "XvRskew"            	# <i>
        #Option     "FpDelay"            	# <i>
        #Option     "Display1400"        	# [<bool>]
        #Option     "Display"            	# [<str>]
        #Option     "GammaBrightness"    	# [<str>]
        #Option     "TVChipset"          	# [<str>]
        #Option     "TVSignal"           	# <i>
	Identifier  "Card0"
	Driver      "trident"
	VendorName  "Trident Microsystems"
	BoardName   "CyberBlade XPAi1"
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

---

