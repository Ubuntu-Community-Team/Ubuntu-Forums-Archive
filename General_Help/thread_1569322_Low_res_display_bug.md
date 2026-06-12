---
title: "Low res display bug"
date: 2010-09-06
forum: General Help
---

### Post by badbob100 on 2010-09-06
Found a problem, on a laptop it Ubuntu booted into 800x600. I could not select a higher resolution. I tried connected a external monitor (1680x1050 native) into the VGA out of the laptop and rebooted. Again I could only select 800x600.

When the partition manager util came up I could not see the bottom section, I could not delete the existing partitions. I could only see aroundabouts where the "format" button is. I could not resize the partition manager util to refit to screen.

I had to use a Windows XP disc, delete the partition, reboot with Ubuntu CD and do auto partition install in Ubuntu.

I'm currently installing onto the laptop HD and see if videocard is picked up/allowed to use native (1024x768)

Anyway just thought let you guys know.

right booted into Ubuntu from HD...nope can only use 800x600. :-( It's Toshiba A20, Trident CyberAladdin videocard. Is this videocard supported?

---

### Post by badbob100 on 2010-09-06
ok tried "lsipci :grep vga" command and shows this

VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

and ddcprobe shows this

vbe: VESA 2.0 detected.
oem: Trident CYBER 8820
memory: 32768kb
mode: 1280x1024x16m
mode: 1280x1024x64k
mode: 1280x1024x32k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 640x480x16m
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 800x600x32k
mode: 800x600x64k
mode: 640x480x32k
mode: 640x480x64k
mode: 1024x768x256
mode: 1280x1024x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x16
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x60 (text)
mode: 80x60 (text)
mode: 800x600x16
edid: 
edid: 1 3
id: 5082
eisa: TOS5082
serial: 00000000
manufacture: 0 1990
input: analog signal.
screensize: 31 23
gamma: 1.000000
dpms: RGB, no active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@75 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
ctiming: 1280x1024@60
ctiming: 1600x1200@60
dtiming: 1024x768@74
dtiming: 1600x1200@78
monitorname: TOSHIBA Inte
monitorname: rnal Panel

tried xresprobe but can't see any new icon placement. Please help asap need this sorted in 24 hours.

---

### Post by realzippy on 2010-09-06
Install
xserver-xorg-video-trident
and try this xorg.conf file:

```
Section "Device"
 Identifier "Trident Microsystems CyberBlade XPAi1"
 Driver  "trident"
 BusID  "PCI:1:0:0" 
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option  "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Trident Microsystems CyberBlade XPAi1"
 Monitor  "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth  1
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
EndSection

Section "DRI"
 Mode 0666
EndSection
```


*feel free to ask further...

---

### Post by badbob100 on 2010-09-06
thanks, I went into /etc/X11 and could not find any xorg.conf file so I did this

In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.
Now execute the following commands:
user@ubuntu ~# sudo service gdm stop
This command will stop the X.
Now we need to generate the xorg.conf file:
user@ubuntu ~# sudo Xorg -configure
This has generated the file in ~/xorg.conf.new.
We need to make the X using it so we have to put this file inside /etc/X11/
user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
After moving this file to the proper location you can start the X again and see what happens:
user@ubuntu ~# sudo service gdm start

gedit new xorg.config shows this

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
	Load  "dbe"
	Load  "record"
	Load  "extmod"
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

### Post by badbob100 on 2010-09-06
argh won't boot had to use other PC to come here...arghh. Do you have a complete xorg.conf file that I can replace the whole lot and then reboot?

Reinstalling ubuntu on the laptop...argh gotta use xp to delete partition, then reboot linux. What a chore. :-(

and what do you mean by "Install xserver-xorg-video-trident" ?

---

### Post by realzippy on 2010-09-06
Sorry,thats why I wrote **feel free to ask further...*

"Do you have a complete xorg.conf file that I can replace the whole lot and then reboot?"

this is what you should have done;there is no more xorg.conf...
Now you seem to have one,so open it:

```
gksudo gedit /etc/X11/xorg.conf
```

Delete all and paste all from above posting.
Then restart.If something gone wrong,simply delete the file:

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by realzippy on 2010-09-06
*and what do you mean by "Install xserver-xorg-video-trident" ?*

```
sudo apt-get install xserver-xorg-video-trident
```

but this seems to be installed already..

---

### Post by badbob100 on 2010-09-06
woo hoo that's done it brilliant cheers!:D

---

### Post by realzippy on 2010-09-06
...fine.Please set thread as solved.

---

