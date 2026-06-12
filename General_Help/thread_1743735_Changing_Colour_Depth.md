---
title: "Changing Colour Depth"
date: 2011-04-29
forum: General Help
---

### Post by ckeech on 2011-04-29
Hi guys,

I have been looking around a number of different forums and posts RE changing colour modes in Ubuntu. I am running an old windows game in WINE that requires 16bit colours. So I have read that you can't adjust this is WINE and WINE just takes whatever your colour depth is set to in Ubuntu.

So other posts recommended to edit xorg.conf. When I tried this my xorg.conf was blank. I then followed instructions to create a new one. This is where it all went pear shaped. After I created the xorg.conf and edited it. My xorg.conf didn't seem to look like anyone else's that posted theirs up. Here it is:


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
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "dri2"
	Load  "dri"
	Load  "record"
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

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
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


Under "Screen" there appear to be multiple entries, each with a different color depth. Anyway I proceeded to add a line “DefaultDepth 16” into the entry so “Screen” section became:

Section "Screen" 
	Identifier "Screen0" 
	Device     "Card0" 
	Monitor    "Monitor0" 
	DefaultDepth 16 
	SubSection "Display" 
		Viewport   0 0 
		Depth     1
[and left everything before and after this the same]

Now when I restarted, logged out and then in all the colours went all over the place. So badly that you couldn't navigate the screen at all. Interestingly if you opened a window, the top of it where the minimize maximise and close buttons are show up fine. I have attached photos of what it looked like before and after.

Any ideas why this is happening? Thanks!

---

