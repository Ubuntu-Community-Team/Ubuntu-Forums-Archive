---
title: "Help! Running a script after resuming from suspending (Ubuntu 10.10 Maverick Meerkat)"
date: 2010-10-13
forum: General Help
---

### Post by fredbsantos on 2010-10-13
Hi! I'm a newbie here! :D
These forums have been my bible ever since I switched from windows to ubuntu... especially because I was so scared that my laptop was always hot (if you know how to change the temperatures at which HP dv7 laptop fans start kicking the hell in- let me know!). 10.10 has improved this so I'm really really happy with this. Seriously love Ubuntu. Okay, enough for intros.

```
sleep 5
xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Palm Detection" 0
xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Tap Action" 1 1 1 1 1 2 3
xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Click Action" 1 1 2
xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Scrolling" 1 0
xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Width" 5
xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Pressure" 3
xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Jumpy Cursor Threshold" 500
xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Scrolling Distance" 250 350
xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Edge Scrolling" 0 0 0
xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Finger" 35 40 255
xinput --set-prop --type=float --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Move Speed" 0.5 0.8 0.001 40
```

I created the following file in /etc/pm/sleep.d but didn't work.
```
#!/bin/sh

# Two-Finger Scrolling after suspending

case "${1}" in
	resume|thaw)
		sleep 5
		xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Palm Detection" 0
		xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Tap Action" 1 1 1 1 1 2 3
		xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Click Action" 1 1 2
		xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Scrolling" 1 0
		xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Width" 5
		xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Pressure" 3
		xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Jumpy Cursor Threshold" 500
		xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Scrolling Distance" 250 350
		xinput --set-prop --type=int --format=8 'SynPS/2 Synaptics TouchPad' "Synaptics Edge Scrolling" 0 0 0
		xinput --set-prop --type=int --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Finger" 35 40 255
		xinput --set-prop --type=float --format=32 'SynPS/2 Synaptics TouchPad' "Synaptics Move Speed" 0.5 0.8 0.001 40
		;;
	
esac
```


I want to run this after resuming from suspending. I've been successful in running the script on startup but couldn't do anything about resuming from suspending with these methods ([http://wiki.ubuntuforums.org/showthread.php?t=1484156](http://wiki.ubuntuforums.org/showthread.php?t=1484156) and every other in the forums).

By the way, these commands enable Two-Finger Scrolling (doesn't work if you put both your fingers in an horizontal line or vertical).

I'm sorry for asking this, I hate asking for help without being able to contribute anything but I really really would love to make this work and the community here seems very nice.

Have a good day :)

---

### Post by fredbsantos on 2010-10-15
Solution:

Edit /usr/share/X11/xorg.conf.d/50-synaptics.conf and insert

```
Option "PalmDetect" "0"
#	Option "Tap Action" "1 1 1 1 1 2 2"
Option "RTCornerButton" "1"
Option "RBCornerButton" "3"
Option "LTCornerButton" "8"
Option "LBCornerButton" "9"
Option "TapButton1" "1"
Option "TapButton2" "2"
Option "TapButton3" "2"
#	Option "Click Action" "1 1 2"
Option "ClickFinger1" "1"
Option "ClickFinger2" "3"
Option "ClickFinger3" "2"
#	Option "Two-Finger Scrolling" "1 0"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "0"
#	Option "Two-Finger Width" "5"
Option "EmulateTwoFingerMinW" "5"
#	Option "Two-Finger Pressure" 3"
Option "EmulateTwoFingerMinZ" "3"
Option "Jumpy Cursor Threshold" "250"
#	Option "Scrolling Distance" "250 350"
Option "VertScrollDelta" "250"
Option "HorizScrollDelta" "350"
#	Option "Edge Scrolling" "0 0 0"
Option "VertEdgeScroll" "off"
Option "HorizEdgeScroll" "off"
Option "CornerCoasting" "off"
#	Option "Finger" "35 40 255"
Option "FingerLow" "35"
Option "FingerHigh" "40"
#	Option "Move Speed" "0.5 0.8 0.001 40"
#Option "MinSpeed" "0.5"
#Option "MaxSpeed" "0.8"
#Option "AccelFactor" "0.001"
```

This is the only way it works. Even if you suspend, hibernate, whatever you do. Also works for the login screen and I assume for all users by default.

---

### Post by doruktayfun on 2010-10-16
These 2 solutions didn't work for me . 
The computer wakes up from sleep 2 finger scroll works for a couple of seconds then the default touchpad options crawls back in. 


So for a temporary fix I made a keyboard shortcut to a shell script I made . which goes like this 
```

#!/bin/bash
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48

```

then using applications->system->keyboard shortcuts I made a shortcut to this shellscript (which I had placed under /home/me/.local/share )
gave it windowsbutton+s shortcut. 
So now whenever 2 fingerscrolling doesn't work i press win+s and it works. 
Very primitive I know , but this was what I could come up with so far.

---

### Post by fredbsantos on 2010-10-17
Yeah it's not the solution after all, that sucks. I'd have to know where the mouse options that kick in are so I could edit them...

---

### Post by oew on 2010-10-24
I have a similar problem. For me it's the TapButton settings that are incorrect after boot and resume from suspend. Tried editing /usr/share/X11/xorg.conf.d/50-synaptics.conf, but it changes nothing. I can use the synclient command to change settings, so the synaptics driver is loaded. I've made a script that i run with Gnome-Do as a temporary solution, but it's to much hassle for me :P

---

### Post by x201r on 2010-10-26
This is similar to my situation in [http://ubuntuforums.org/showthread.php?t=1606576](http://ubuntuforums.org/showthread.php?t=1606576)

Seems like the default touchpad settings end up overwriting our tweaks

---

### Post by banstew on 2010-10-27
> **fredbsantos said:**
> Solution:

Edit /usr/share/X11/xorg.conf.d/50-synaptics.conf and insert

```
Option "PalmDetect" "0"
#    Option "Tap Action" "1 1 1 1 1 2 2"
Option "RTCornerButton" "1"
Option "RBCornerButton" "3"
Option "LTCornerButton" "8"
Option "LBCornerButton" "9"
Option "TapButton1" "1"
Option "TapButton2" "2"
Option "TapButton3" "2"
#    Option "Click Action" "1 1 2"
Option "ClickFinger1" "1"
Option "ClickFinger2" "3"
Option "ClickFinger3" "2"
#    Option "Two-Finger Scrolling" "1 0"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "0"
#    Option "Two-Finger Width" "5"
Option "EmulateTwoFingerMinW" "5"
#    Option "Two-Finger Pressure" 3"
Option "EmulateTwoFingerMinZ" "3"
Option "Jumpy Cursor Threshold" "250"
#    Option "Scrolling Distance" "250 350"
Option "VertScrollDelta" "250"
Option "HorizScrollDelta" "350"
#    Option "Edge Scrolling" "0 0 0"
Option "VertEdgeScroll" "off"
Option "HorizEdgeScroll" "off"
Option "CornerCoasting" "off"
#    Option "Finger" "35 40 255"
Option "FingerLow" "35"
Option "FingerHigh" "40"
#    Option "Move Speed" "0.5 0.8 0.001 40"
#Option "MinSpeed" "0.5"
#Option "MaxSpeed" "0.8"
#Option "AccelFactor" "0.001"
```This is the only way it works. Even if you suspend, hibernate, whatever you do. Also works for the login screen and I assume for all users by default.

Do you just insert it below the endSection for "input class" or in the actual section part 

```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
EndSection
```

That is what I have initially

---

### Post by fredbsantos on 2010-11-23
Change the name of that file. Whichever number it has, put it 99. For example, if it's 50-xxxxxxx put 99-xxxxxxx.

I fixed it by learning that the higher the number, the higher the priority. Imagine that there's a default file numbered 60-xxxxxxx and your custom config being 50-xxxxxx, yours will be overwritten. 99 is the maximum!


Hope it helped somehow. :)

---

### Post by kslen on 2010-12-09
Check out post #1 and #6 over at [http://ubuntuforums.org/showthread.php?p=10220575#post10220575]("http://ubuntuforums.org/showthread.php?p=10220575#post10220575").

This will most likely resolve your trouble.

---

