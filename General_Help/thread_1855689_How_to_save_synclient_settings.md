---
title: "How to save synclient settings"
date: 2011-10-06
forum: General Help
---

### Post by Ralph L on 2011-10-06
I changed a number of synclient settings to make my touchpad work better.  However, when I restarted the computer all my changes were lost.  Is this normal?  Is there a way I can make permanent the changes I made with synclient?

Any help appreciated?
Ralph

---

### Post by Ralph L on 2011-10-07
To make changes permanent I used instructions from this site [http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings](http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings)

Originally Posted by NoBugs! View Post
run:
Code:

sudo gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf

then find the touchpad section and add these 6 lines to it:
Code:

Section "InputClass"
Identifier "touchpad catchall"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Driver "synaptics"

Option "JumpyCursorThreshold" "90"
Option "AreaRightEdge" "5800"
Option "FingerLow" "44"
Option "FingerHigh" "45"
Option "PalmDetect" "1"
Option "Minspeed" ".2"

EndSection

Save and restart and it will work

---

### Post by Ralph L on 2012-12-02
Error in the above settings: Minspeed should be MinSpeed.  Other references:
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)
[http://www.yeap.de/blog2.0/archives/84-Configuring-the-Synaptics-Touchpad.html](http://www.yeap.de/blog2.0/archives/84-Configuring-the-Synaptics-Touchpad.html)

---

### Post by Ralph L on 2013-03-26
Note that in newer systems the location on xorg.conf.d has changed.  You may need to do a search on the "File System" to find it.  In addition the prefix number for the synaptics.c file may have changed.  This was the latest file location that I was aware of:

sudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf

Most recently I have made synclient settings permanent by putting a scipt file with synclient commands in the startup applications.

---

