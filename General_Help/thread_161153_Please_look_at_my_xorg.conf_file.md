---
title: "Please look at my xorg.conf file"
date: 2006-04-16
forum: General Help
---

### Post by lonelypauly on 2006-04-16
I have 2 identical monitors hooked to my GeForce6800 (PCI-E) but only one is working....the other monitor looks like this:

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/img_0618.jpg[/IMG]

What should I do to my config file to fix this?  How can I run Nvidia TwinView so as to have it in span mode where I can be free to drag windows across monitors if needed?  I will paypal 10 bucks to the first person that helps me (to my satisfaction) get my other monitor working AND be able to use Twinview as described above.  Thanks.  


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"GatewayVX112"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"GatewayVX112"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by IYY on 2006-04-16
To get Twinview working, you'll first need to install the official nvidia driver.

```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

```

Once you do that, use the following, changes in bold:

```
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
Driver "**nvidia**"
BusID "PCI:5:0:0"
[B]
Option "TwinView" "on"
Option "MetaModes" "1920x1440,1920x1440"
Option "TwinViewOrientation" "LeftOf" 
Option "SecondMonitorHorizSync" "31.4-68.6"
Option "SecondMonitorVertRefresh" "59-85"
Option "RenderAccel"    "true"
Option "NoLogo" "True"[/B]
EndSection

Section "Monitor"
Identifier "GatewayVX112"
Option "DPMS"
[B]Option "HorizSync" "30-85"
Option "VertRefresh" "50-160"[/B]
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
Monitor "GatewayVX112"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection
```

NOTE: I guessed the resolutions of your monitors, you should use whichever resolutions are supported/you want. Same goes for the refresh rates! You need to find out the refresh rates (vertical and horizontal) that are right for your monitors, and use those (you will find this information in your monitor's manual, or just in the monitor's settings).

---

