---
title: "is there any way to force a resolution?"
date: 2011-04-09
forum: General Help
---

### Post by edemark on 2011-04-09
Hello everyone,

I am trying to force a resolution (800x600) through xorg.conf. How to do that? The story is the following. I am trying to play a game (theocracy) on my toshiba nb100 (max resolution (1024x600) however the game supports only 800x600 resolution. To play I am using xgame ([http://freshmeat.net/projects/xgame/](http://freshmeat.net/projects/xgame/)) which has the option to use a separate xorg.conf file to run the game. Even though I created a new xorg.conf1 file which only contains in its "screen" section Modes "800x600" notwithstanding the new screen, with the game is set to 1024x600. 
So the question is how to force 800x600 through the xorg.conf.

Thanks in advance

---

### Post by linuxuser12345 on 2011-04-09
Here is a similar topic that may help you out:
[http://ubuntuforums.org/showthread.php?t=1724680](http://ubuntuforums.org/showthread.php?t=1724680)

---

### Post by KegHead on 2011-04-09
Hi!

Just guessing..Goto:

system...preferences..monitor.

KegHead

---

### Post by 5149.5 on 2011-04-09
If the monitor application doesn't offer the desired setting, you could change the setting with the xrandr command using terminal.

---

### Post by edemark on 2011-04-11
Hi, first thanks for all the feedbacks and sorry for the slow reply (i was really occupied). So I am still not there with this issue. Dear 5149.5 I cannot use xrandr as the xgame program can only use xorg.conf files. Dear KegHead similar problem with your approach, because xgame (through the use the xorg.conf file) starts up the game so there is no way of changing other settings. Finally, dear linuxuser12345 sadly the suggested page did not help me to resolve my problem. So please if any other ideas just let me know to try it out.
Anyway, thanks again for your replies (it is always good to see that the community works)

---

### Post by KegHead on 2011-04-11
in xorg.conf

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Virtual 1024 768
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

add virtual specs--ie virtual 1024 768
make sure mode is added.

Let me know if this works!

KegHead

---

### Post by edemark on 2011-04-13
Hello KegHead

sorry for the slow reply. I thought that the easiest would be if I attach my xorg.conf file. As you can observe there is only one mode 800x600 however the screen comes up 1024x600.

Any idea?
Thanks again

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
	Load  "dri2"
	Load  "record"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
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
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth    16
	SubSection     "Display"
        Depth       16
        Modes      "800x600" 
	Viewport   0 0
	EndSubSection
EndSection

---

### Post by KegHead on 2011-04-13
Hi1

Under subsection display..add:

virtual 800 600

save
sample:

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Virtual 800 600
Modes "1024x600" "800x600" "640x480"
EndSubSection
EndSection

Restart

Should work.

KegHead

---

### Post by Blackoulis on 2011-04-13
Why don't you run it on a virtual desktop?

---

### Post by edemark on 2011-04-13
Hello again,

Dear Blackoulis xgame actually starts up a new virtual desktop and runs the game in that new virtual desktop.
Dear Keghead, if I use the line virtual 800 600, then the game starts in 640x480. Actually, could it be that as in monitor preferences, which can be found in system/preferences only two resolution exists (1024x600 and 640x480) it affects the virtual screen also? (just to be clear again I am using the xorg.conf based set up only for this xgame script but not to have the "normal" screen, in general terms, set up)

thanks again for the help

---

### Post by edemark on 2011-04-17
Hi everyone,

any idea then that can fix this problem?

---

### Post by edemark on 2011-04-19
So any idea? Anyone? Please!!

---

