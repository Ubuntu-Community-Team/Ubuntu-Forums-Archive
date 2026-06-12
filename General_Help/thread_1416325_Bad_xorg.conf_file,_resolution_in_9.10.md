---
title: "Bad xorg.conf file, resolution in 9.10"
date: 2010-02-25
forum: General Help
---

### Post by Hydrargyri on 2010-02-25
Hello everyone,

I have recently shifted from 8.04 to 9.10, and I have just recently encountered a problem.

In short, my screen is stuck at 640x480! I cannot increase the resolution beyond that. My monitor is a 17 inch HD, so it only looks nice when its 1440x900 resolution.

What's strange is that I *did* have the best resolution, but after a crashing bootup, the resolution reverted to, well, 640x480.

I have looked through a variety of threads in this forum and others. I'm sorry for having to create a new thread, but all of the others were listed as "resolved", yet seemingly cannot resolve my issue.

The following is basically a huge amount of information that other threads found important. I post this simply to hopefully address any "starter" questions, so as to be the least bother possible. :)

(Note: I'm comfortable enough with terminal commands, etc., but I'm really out of my league when it comes to modifying init and config files and who-knows-what else, which is why I turn to you all for help.)

Following the instructions here: [http://ubuntuforums.org/showthread.php?t=1370258&highlight=resolution](http://ubuntuforums.org/showthread.php?t=1370258&highlight=resolution)
I find that everything works up until I try to set the output, in which case I get an error message. Here is the full terminal:

```
aaron@aaron-desktop:~$ xrandr
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
aaron@aaron-desktop:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
aaron@aaron-desktop:~$ xrandr --newmode "1440x900_60.00"  106.50 1440 1528 1672 1904  900 903 909 934 -hsync +vsync
aaron@aaron-desktop:~$ xrandr --addmode default 1440x900_60.00aaron@aaron-desktop:~$ xrandr --output default --mode 1440x900_60.00xrandr: screen cannot be larger than 640x480 (desired size 1440x900)
```


I have changed drivers (there are 2 proprietary ones, I switch between them multiple times), tried to create a new xorg.conf file (both manually and through Xorg -configure).

In other threads it appears that the Xorg error log is handy, I have included all of the warnings (there were no errors), here is the latest:

```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(WW) NVIDIA(0): No valid modes for "1440x900"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.

```

Here is a grep of VGA from my lspci command:
06:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)

Lastly, here is a cat from my xorg.conf file. Note that this was automatically created via Xorg -configure, and then I added the "modelines" at the bottom specifying the resolution in a repeated, vain attempt to address this issue myself.

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
	Load  "dri2"
	Load  "glx"
	Load  "record"
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
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "G84 [GeForce 8600 GT]"
	BusID       "PCI:6:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes "1440x900"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes "1440x900"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes "1440x900"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes "1440x900"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1440x900"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1440x900"
	EndSubSection
EndSection

```

Lastly, when I go to system->administration->drivers, here are the restricted drivers listed:
NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version 185) [Recommended]

I have 173 selected currently, because that was the one that was working. I have tried the other, as well as none of them.

I thank you all preemptively for the help!

---

### Post by Barriehie on 2010-02-25
Have you tried **dexconf**?

---

### Post by Hydrargyri on 2010-02-26
Hi Barriehie, thanks for the speedy reply.
I ran that command, and it produced a file /xorg.config.new, but it is a completely empty file. I tried an empty config file before, and it didn't help. Is dexconf supposed to produce something else?

---

### Post by Barriehie on 2010-02-26
> **Hydrargyri said:**
> Hi Barriehie, thanks for the speedy reply.
I ran that command, and it produced a file /xorg.config.new, but it is a completely empty file. I tried an empty config file before, and it didn't help. Is dexconf supposed to produce something else?

No, it should've worked.  I can't remember the situations where it doesn't work!  These 2 threads might help.

[http://ubuntuforums.org/showthread.php?t=1353573&highlight=nvidia+8600](http://ubuntuforums.org/showthread.php?t=1353573&highlight=nvidia+8600)

[http://ubuntuforums.org/showthread.php?t=1291904&highlight=nvidia+8600](http://ubuntuforums.org/showthread.php?t=1291904&highlight=nvidia+8600)

HTH,
Barrie

---

### Post by Hydrargyri on 2010-03-05
Thanks for the additional links, Barriehie. I read through them and tried some of the things they suggested, still no luck. :(

I was wondering if there is a way of completely stripping gnome and re-installing it? I ask this because my resolution *did* work beforehand. Obviously a clean re-install would do this, but is there a quick apt-get command or two that would remove just the relevant parts, and not require nuking the whole drive?

Thanks!

---

### Post by Hydrargyri on 2010-03-05
I'm adding this as a separate post because it is a separate issue. Hoping to glean some more information, I dusted off my liveCD --- the same that I installed it with, and booted from that. While I remember distinctly everything *working* when I first tried the liveCD, this time it never got past the terminal output on the screen, and the screen would flicker! Only "during" a flicker could it read from the keyboard input, and even then only sometimes. This is indeed a very odd error! I looked in my BIOS for any strange video settings, but could find none. What on earth could be going on?

Thanks again, this is quite marvelously confusing...

---

### Post by Barriehie on 2010-03-05
Found a link:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

and another one:
[http://ubuntuforums.org/archive/index.php/t-546952.html](http://ubuntuforums.org/archive/index.php/t-546952.html)

Barrie

---

### Post by Hydrargyri on 2010-04-09
Hello again,
I'd just like to end this thread, I'm sorry for the late reply, I have only been able to devote a little time to this problem over the weeks.

In short, it *was* a hardware error! I snagged another monitor, and it was detected perfectly. My understanding is that the "EDID" "chip" or whatever broke on the monitor itself, so that I could not convince ubuntu to treat it other than 600x480.

Thanks for your patience and help, Barriehe!

---

