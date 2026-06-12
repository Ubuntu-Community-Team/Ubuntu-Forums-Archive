---
title: "Wacom tablet pc right click."
date: 2010-08-09
forum: General Help
---

### Post by grindboy on 2010-08-09
Hi Guys,

I've just got ubuntu 10.04 running on my Motion M1400. The default drivers/config for the Wacom tablet were working great except for right click. I've now edited my 10-wacom.conf (apparently the 10.04 version of xorg.conf) to enable right click.

My problem is that in 8.10 (the last OS on my tablet) right click was mapped in such a way that holding down the side button AND tapping the screen produced a right click. In 10.04 just tapping the side button produces a right click.

The 8.10 version was useful for gestures etc.  So my question is. How do I edit the config file so that holding the side button & tapping the screen results in a right click?

Hope that all makes sense (I'm tired, its been a long day so feel free to ask for clarification on anything).

Cheers

Grindboy

---

### Post by Favux on 2010-08-09
Hi grindboy,

Sounds like you need to add:
```
Option  "TPCButton"  "on"
```
just before:
```
Option  "Button2"  "3"
```
in the serial snippet in 10-wacom.conf you are editing.

---

### Post by grindboy on 2010-08-09
Favux, once again you have proved yourself to be the undisputed champion of ubuntu tablet computing. Thank you again! :-)

---

### Post by Nurionn on 2010-08-18
I own a MotionComputing M1400, too. Could you please post your xorg.conf?

---

### Post by psankovic on 2010-08-30
> **Favux said:**
> Hi grindboy,

Sounds like you need to add:
```
Option  "TPCButton"  "on"
```
just before:
```
Option  "Button2"  "3"
```
in the serial snippet in 10-wacom.conf you are editing.

hi,

my 10-wacom.conf looks like this.Where do I put ...TPvbutton part

Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

thanks

---

### Post by Favux on 2010-08-30
Hi psankovic,

What kind of tablet pc do you have?  Is it serial or usb?

---

### Post by psankovic on 2010-08-30
it's motion computing m1400, do not know if it's serial or usb.

---

### Post by Favux on 2010-08-30
It's serial.  So it would be in the serial snippet:
```
Section "InputClass"
Identifier "Wacom serial class"
MatchProduct "Serial Wacom Tablet"
Driver "wacom"
Option "ForceDevice" "ISDV4"
Option  "TPCButton"  "on"
EndSection
```

---

### Post by psankovic on 2010-08-30
> **Favux said:**
> It's serial.  So it would be in the serial snippet:
```
Section "InputClass"
Identifier "Wacom serial class"
MatchProduct "Serial Wacom Tablet"
Driver "wacom"
Option "ForceDevice" "ISDV4"
Option  "TPCButton"  "on"
EndSection
```

I have put it there but it's still not working. Do I need to set enything else?

/thanks

---

### Post by Favux on 2010-08-30
What's not working?  If you want the right click you have to add:
```
Section "InputClass"
Identifier "Wacom serial class"
MatchProduct "Serial Wacom Tablet"
Driver "wacom"
Option "ForceDevice" "ISDV4"
Option  "TPCButton"  "on"
Option  "Button2"  "3"
EndSection
```

---

### Post by psankovic on 2010-08-30
thanks. you are genius.
since you know about this stuff can you give me pointer on how to configure
1. side buttons for screen rotating, and rest of them are not working at all. how do i configure them
2. is there any good character recognize software
3. on win xp when i clicked on virtual keyboard window below were automatically reduced so everything fit to screen. is something like that possible on ubuntu.

many, many thanks for help

---

### Post by Favux on 2010-08-30
Hi psankovic,

You're welcome.

> 1. side buttons for screen rotating, and rest of them are not working at all. how do i configure them
If they give off a keycode in xev then you can keybind them to a rotation script.  Method's 1 or 3 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") should work, along with more explanation on key binding.
> 2. is there any good character recognize software
CellWriter.  It also serves as your onscreen keyboard.  You'll also want Xournal.  And for gestures (like flicks) EasyStroke.
> 3. on win xp when i clicked on virtual keyboard window below were automatically reduced so everything fit to screen. is something like that possible on ubuntu.
Not sure what you're asking for here.  I have a launcher that brings up CellWriter in the size and location I want when I click on it.  Otherwise I have it set up to be hidden in landscape and to be visible on the edge of the screen in portrait (rotated).

---

### Post by psankovic on 2010-08-31
hi

Do you know is where can I find manual or some other documentation with explanation on how to configure 10-wacom.conf file. I think there is more possibility in this file than what am I currently using. e.g. eraser...

One other question do you know is Motion M1400 support automatic screen rotation ( when I rotate tablet, screen orientation will follow) or only button rotation is possible.

Thanks

---

### Post by Favux on 2010-08-31
> Motion M1400 support automatic screen rotation ( when I rotate tablet, screen orientation will follow)
I don't think the Motion has an accelerometer, so you won't be able to do that.  I'm not 100% sure though.

With the current .conf file setup you can't configure dependent devices like the eraser.  The way to do that is to use a xetwacom startup script.  See the sample .xsetwacom.sh for the TX2000 attached to the second post at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  It should basically work for you if you remove the touch section and rename the "Device names" to what:
```
xinput --list
```
calls your devices.  Instructions are in IV. of the HOW TO.

---

