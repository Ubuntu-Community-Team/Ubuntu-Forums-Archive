---
title: "Help With Dual Monitors"
date: 2006-02-24
forum: General Help
---

### Post by Ujeni on 2006-02-24
Hey Everyone,

I'm new to Ubuntu, but I gotta say...this is the best distribution of Linux that I have tried yet. In less than an hour I had my disk repartitioned, ubuntu installed, ati drivers installed, Maya 7 running and even watched a DVD. That took a long time with Suse :)

Anyway, I am now having a little trouble with my dual monitor setup. I have two dell 2001fp (1600x1200) monitors and would like to treat them as one desktop. Here is what I have done:

1. Installed Ubuntu 5.10
2. Installed the ATI drivers (I have an ATI 9800 pro). I have confirmed that they worked (both with glxgears and with fglrxinfo)
3. I tried to use the ATI control panel to set up my dual monitors but no changes took effect after restarting. So I did this in the terminal:

sudo aticonfig --initial=dual-head --screen-layout=rightof

Now I have the two monitors working, but it seems like it is two different desktops, not one big one that spans both monitors (i can't drag a window from on to the other but my cursor can move between them just fine). Any ideas?

Here's my xorg.conf:


[INDENT]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	Screen         "aticonfig Screen 1" RightOf "aticonfig Screen 0"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "DELL 2001FP"
	HorizSync    30.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 1"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor    "DELL 2001FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 1"
	Device     "ATI Graphics Adapter 1"
	Monitor    "aticonfig Monitor 1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection[/INDENT]

Thanks in advance for your advice! :)

---

### Post by LycoLoco on 2006-02-24
Try adding these to your first display section:
```
        Option          "TwinView"      "on"
        Option          "TwinViewOrientation"           "RightOf"
```
And this under the screen section
```
        Option          "MetaModes"     "1280x1024, 1280x1024"
```

Taken from this thread: [http://ubuntuforums.org/showthread.php?t=135567&highlight=twinview](http://ubuntuforums.org/showthread.php?t=135567&highlight=twinview)

---

### Post by Ujeni on 2006-02-24
Isn't twinview for nvidia cards? I have an ATI card.

---

### Post by bazcor on 2006-02-25
Have you tried 'sudo fglrxconfig' this worked for me.

---

### Post by Ujeni on 2006-02-25
[QUOTE=bazcor]Have you tried 'sudo fglrxconfig' this worked for me.[/QUOTE]

Yes, it says "command not found"

---

### Post by Jindro on 2006-02-27
Hi Ujeni,

my xorg.conf works (in Breezy), look at:

[http://www.ubuntuforums.org/showthread.php?t=135624&highlight=xorg](http://www.ubuntuforums.org/showthread.php?t=135624&highlight=xorg)

---

### Post by snovak on 2008-01-23
This should work.. 

Or you can look at the differences and edit yours.

[http://www.snovak.com/content/view/46/49/]("http://www.snovak.com/content/view/46/49/")

---

