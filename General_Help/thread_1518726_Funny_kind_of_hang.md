---
title: "Funny kind of hang"
date: 2010-06-27
forum: General Help
---

### Post by haider.malik on 2010-06-27
My 10.04 LTS randomly hangs and the situation on screen gets kind of funny. It keeps switching between a black screen with some text on it (which i am unable to read because of speed) and another black screen of different resolution with some gray horizontal lines (made of ascii block character) at top left. :D I have to hard reboot every time. :(

---

### Post by stderr on 2010-06-27
Hi. Sounds like a video driver issue. Could you post the output of:

```
lshw -c video
```

Also, should it occur again, you can try various things before resorting to the ahrd reboot. For example, magic keys (explained in some detail [on wikipedia]("http://en.wikipedia.org/wiki/Magic_SysRq_key")), which can normally perform safe reboots even when all hope is lost! The gist is to hold down Alt AND PrintScreen (otherwise known as SysRq), AND then type slowly the 6 letters R E I S U B. Each has a specific action explained on the page.

---

### Post by haider.malik on 2010-06-27
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6fffff

---

### Post by stderr on 2010-06-27
Hmm odd, normally you'd have a driver name under "configuration:". For example, part of my output:

```
[...]
capabilities: bus_master cap_list rom
configuration: driver=nvidia latency=0

```

Could you post the output of xorg.conf?

```
cat /etc/X11/xorg.conf
```

If you're running the default "intel" driver, you may have more luck rolling back to an earlier version ([here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")).

---

### Post by stderr on 2010-06-27
This is probably what you're looking for [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

Looks like using the "vesa" driver instead should work, but then again you'll have no 3D accn etc. But if the system's still responsive enough under vesa that may be the way to go for the time being.

---

### Post by haider.malik on 2010-06-27
I don't have xorg.conf at /etc/X11/. I generated it by giving configure command and it placed it in my home directory. Here it is:

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
	Load  "extmod"
	Load  "record"
	Load  "glx"
	Load  "dbe"
	Load  "dri2"
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
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
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

---

