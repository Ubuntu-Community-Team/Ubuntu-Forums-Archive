---
title: "External Monitor"
date: 2010-04-23
forum: General Help
---

### Post by Monotoko on 2010-04-23
Hiya Guys, i was wondering if you could help me with an issue i have been having.

My laptops screen has recently gained an annoying blue tint, which i do not have the expertise (or money to pay somebody) to fix, so i am using my TV as an external monitor.

So what i am proposing to do is purely use the External and leave the laptop monitor off.

I am dual-booting Windows XP and Ubuntu 10.04 Devel, 

In XP it was a simple case of right clicking the Intel Graphics Media Accelorator and choosing the External Monitor option, this then allowed me to set my resolution to 1280x960 and i was happy.
(even bigger desktop than before actually)

I cannot seem to find this option in Ubuntu, going through
System -> Prefrences -> Monitor gives me the option to mirror
the screens, but that leaves me with an incredibly low resolution, choosing to not mirror the screens allows me to set the resolution to 1280x960, but the LCD screen still acts as my main.

Is there any way I can set it to recognise the TV as the main, and switch off the LCD like I did in Windows?

---

### Post by Monotoko on 2010-04-23
anyone..?

---

### Post by Monotoko on 2010-04-23
I thought this would be an easy question?

---

### Post by quadproc on 2010-04-23
> **Monotoko said:**
> 
...
Is there any way I can set it to recognise the TV as the main, and switch off the LCD like I did in Windows?
I don't know enough about your system to know for sure if this will work, but I think that you can modify your xorg.conf file to specify the characteristics of your displays.  You can use BusID on the one that you want to be the primary device.  I believe that there is also an option to disable a display and you could use that on the built-in screen.  Sorry that I don't have enough details to tell you exactly what you need in the file but Google and the manual for X windows probably will.

quadproc

---

### Post by Monotoko on 2010-04-23
I don't feel very confident using xorg or X and modifying config files, i always seem to break it ^.^

Can you tell me what information you need?

---

### Post by veli on 2010-04-23
What's your video card? If it's Nvidia, you can install nvidia-settings package in synaptic, and then it's easy to configure the monitor. I did it already with my laptop. No idea about other video card, but most likely you have to edit the xorg file.

---

### Post by Monotoko on 2010-04-23
Its an integrated Intel one...

An Intel® 945G Express Chipset i do believe. Is there anything equivilant for it?

---

### Post by quadproc on 2010-04-23
> **Monotoko said:**
> I don't feel very confident using xorg or X and modifying config files, i always seem to break it ^.^

Can you tell me what information you need?
The xorg.conf file usually isn't very big so you could paste it into a posting here and wrap CODE tags around it so that it will be easier to read.  I suppose that you could also attach your xorg.conf file to a post.

A good defense against a broken xorg.conf is to keep a backup copy of whatever was working.  So, for example, you could do:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
```Then edit the xorg.conf file with privilege.  If the result doesn't work then from recovery mode you can
```
cd /etc/X11
sudo mv xorg.conf.backup xorg.conf
```Another possibility for recovering is to simply rename the xorg.conf file to something else if your Ubuntu version is late enough. Ubuntu 9.10's version of X windows doesn't require an xorg.conf file and, if the file doesn't exist, will survey the hardware and try to do what makes sense.

quadproc

---

### Post by Monotoko on 2010-04-23
Okay, i didnt have one originally, but i managed to generate one in single-user mode.

Although im not quite sure what needs doing with it :/
Here it is:

```
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
	Load  "record"
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
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
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
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

```

---

### Post by Monotoko on 2010-04-23
Solved, i didnt see the tickbox to turn the laptop screen off, which magically made my external moniter my primary...

Hopefully my daft mistake can help others XD

---

### Post by quadproc on 2010-04-23
> **Monotoko said:**
> Solved, i didnt see the tickbox to turn the laptop screen off, which magically made my external moniter my primary...

Hopefully my daft mistake can help others XD

I see that your Intel graphics has a BusID and an Intel driver.  Those were the things that I would have been primarily interested in.

I am glad that your solution turned out to be so simple.  Thanks for letting us know!

quadproc

---

