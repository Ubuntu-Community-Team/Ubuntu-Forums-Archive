---
title: "ACECAD Graphics Tablet"
date: 2010-01-06
forum: General Help
---

### Post by DGoose on 2010-01-06
Hello all,

I'm looking for help with an ACECAD Flair II GT-504 USB graphics tablet that I am attempting to use in Karmic Koala. I tried installing the [ACECAD specific driver]("http://acecad.sourceforge.net/") a while back and couldn't get it to work. So I gave up. Decided I'd just keep using Windows for image editing. Well, due to unforeseen and irreparable damage to my machine, I can no longer boot Windows. So. Here I go again looking for ways to get this tablet to work in Ubuntu.

I found the [WizardPen tutorial]("https://help.ubuntu.com/community/TabletSetupWizardpen") and since it specifically mentions my tablet as tested and working, I attempted to follow it.

Problem #1: The cursor responds to tablet movements now, just not at a 1:1 ratio with the monitor. I don't know if I'm not calibrating properly or it's just being weird or what, but that is bugging me. It also appears to behave like a mouse instead of a tablet.

Problem #2: None of the buttons work. I've tried to assign the buttons using the "xinput set-button-map" method but it doesn't change anything.

Any and all help is very much appreciated. Attached are my various configs, logs, and results that have to do with this situation. If more is needed just let me know.

Thanks,

---

### Post by Favux on 2010-01-06
Hi DGoose,

The reason it is behaving like a mouse/touchpad is it looks like the evdev driver has it and has configured it as a touchpad.

From the Xorg.0.log:
```
(II) config/hal: Adding input device ACECAD USB Graphics Tablet
(**) ACECAD USB Graphics Tablet: always reports core events
(**) ACECAD USB Graphics Tablet: Device: "/dev/input/event4"
(II) ACECAD USB Graphics Tablet: Found 3 mouse buttons
(II) ACECAD USB Graphics Tablet: Found x and y absolute axes
(II) ACECAD USB Graphics Tablet: Found absolute touchpad
(II) ACECAD USB Graphics Tablet: Configuring as touchpad
(**) ACECAD USB Graphics Tablet: YAxisMapping: buttons 4 and 5
(**) ACECAD USB Graphics Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ACECAD USB Graphics Tablet" (type: TOUCHPAD)
(**) ACECAD USB Graphics Tablet: (accel) keeping acceleration scheme 1
(**) ACECAD USB Graphics Tablet: (accel) filter chain progression: 2.00
(**) ACECAD USB Graphics Tablet: (accel) filter stage 0: 20.00 ms
(**) ACECAD USB Graphics Tablet: (accel) set acceleration profile 0
(II) ACECAD USB Graphics Tablet: initialized for absolute axes.
(WW) ACECAD USB Graphics Tablet: unable to handle keycode 331
(WW) ACECAD USB Graphics Tablet: unable to handle keycode 332
```

This thread might be of some help:  [http://ubuntuforums.org/showthread.php?t=1330098](http://ubuntuforums.org/showthread.php?t=1330098)  Someone to talk to and work on it with anyway.

Hope this helps.

---

### Post by DGoose on 2010-01-07
So I don't know which driver I'm using any more, but my tablet is now working at 99% (I'd like to adjust the sensitivity a little but haven't researched that yet). Anyway, I just changed a couple lines in my xorg.conf file and that did the trick. Attached are the affected files.

---

### Post by Favux on 2010-01-11
Hi DGoose,

Given your xinput you might need something like this:
```
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"TopZ"		"0"
	Option		"BottomX"	"5000"
	Option		"BottomY"	"3800"
	Option		"BottomZ"	"511"
	Option		"MaxX"		"5000"
	Option		"MaxY"		"3800"
	Option		"MaxZ"		"511"
```
But given your xinput, Xorg.0.log, and lshal the evdev driver has your tablet, so you probably need a .fdi.  I don't think your xorg.conf is doing anything.

---

