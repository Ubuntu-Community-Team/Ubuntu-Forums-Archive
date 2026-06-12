---
title: "Intel 82915G/GV/910GL VGA on 9.10"
date: 2009-11-11
forum: General Help
---

### Post by true_friend on 2009-11-11
Hi Folks
I am using above listed VGA card and Ubuntu 9.10. But I am unable to get correct resolution. It only shows 400*600. I searched various sites, ubuntu forums etc and found that intel graphics cards less work with Ubuntu. I have tried various solutions but invain. Interesting thing is that there is no /etc/X11/xorg.conf file in my system. So I was unable to apply manual configuration as it was suggested in some threads. I tried to do it by 
sudo dpkg-reconfigure xserver-xorg
but it simply blinks the screen once and thats all. According to the searches I found that this VGA was working on previous version of Ubuntu but now its in worst condition.
Any ideas to solve this problem?

---

### Post by ST3ALTHPSYCH0 on 2009-11-12
If you have an xorg.conf file it will try to use it. You can generate an entire xorg.conf file for your computer using a tool included in the 8.04LTS CD (if you don't know how from scratch) [like this](http://ubuntuforums.org/showthread.php?p=8280317#post8280317).

---

### Post by true_friend on 2009-11-12
Ok I've generated a default looking xorg.conf file by Xorg -configure
Here it is.
> Section "ServerLayout"
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
	Load  "dbe"
	Load  "dri2"
	Load  "record"
	Load  "glx"
	Load  "dri"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
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
	VendorName  "Intel Corporation"
	BoardName   "82915G/GV/910GL Integrated Graphics Controller"
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

Now how to add my monitor and VGA card information?
ps: I was pleased to see the driver working fine in Kubuntu 8.04 as I tried to generate an xorg.conf file from it as it was done [here]("http://ubuntuforums.org/showthread.php?p=8280317#post8280317") from Ubuntu 8.04. Couldn't do this.

---

### Post by ST3ALTHPSYCH0 on 2009-11-13
Interesting, I had read that the devs took that tool out because it would sometimes screw up the config file. I have also read that Intel doesn't play nicely with xorg.conf, and you need to instead use the xrandr command. I'll try to find those links and edit them into this post.

In the meantime, read post #38 on [this]("http://ubuntuforums.org/showthread.php?t=1319491&page=4;%20postcount=38") page to see how to start getting your monitor spec into the xorg.conf file.

EDIT: Read [post #5](http://ubuntuforums.org/showthread.php?t=1321224) to see how to use cvt+xrandr to configure your resolution.
Good luck!!!

---

### Post by true_friend on 2009-11-15
ok. solved with the help of above post of ST3ALTHPSYCH0 (Thanks Buddy :) ) I m able to see my desktop in 1352*864 resolution which same as my windows xp desktop has.
Regards

---

### Post by true_friend on 2009-11-15
ok. solved with the help of above post of ST3ALTHPSYCH0 (Thanks Buddy :) ) I m able to see my desktop in 1352*864 resolution which same as my windows xp desktop has.
Regards

---

