---
title: "mouse touchbad ubutu 11.10"
date: 2012-04-13
forum: General Help
---

### Post by miz0ooo0 on 2012-04-13
[SIZE=2]i installed ubuntu 11.10 day ago ,and now i don't find any touch bad setting to enable 2 fingers scrolling in my laptop  (DELL n5110) .
in the mouse & touch bad setting i find one tab only "mouse" but when i searched the internet i found that there are 2 tabs "mouse" and "touch bad ", am i installed the wrong version of ubuntu "desktop" instead of "laptop" ?
and if that what i can do to fix this?
thnx for advance :)

[/SIZE]

---

### Post by anejo on 2012-04-13
Installing 'xserver-xorg-input-synaptics' should sort out the touchpad
and the Ubuntu releases are the same whether you install them on laptops or whatever

---

### Post by miz0ooo0 on 2012-04-13
> **anejo said:**
> Installing 'xserver-xorg-input-synaptics' should sort out the touchpad
and the Ubuntu releases are the same whether you install them on laptops or whatever
"xserver-xorg-input-synaptics" is already installed ,but i dont find any settings for touchpad

---

### Post by anejo on 2012-04-14
Well thats the role of that xserver mod...
>  * Dragging through short touching and holding down the finger on the touchpad
 * Middle and right button events on the upper and lower corner of the touchpad
 * Vertical scrolling through moving the finger on the right side of the touchpad
 * Horizontal scrolling through moving the finger on the lower side of the touchpad
 * Adjustable finger detection
Selecting 'System Settings' should display a 'Mouse and TOUCHPAD' option!

---

### Post by miz0ooo0 on 2012-04-15
i know how to scroll in this situation but i liked scrolling with 2 fingers i see it much easier ,concerning touchbad option unfortunately i don't find it in the setting ,there is only one tab for mouse 
[IMG]http://img820.imageshack.us/img820/4690/screenshotat20120415122.png[/IMG]

---

### Post by miz0ooo0 on 2012-04-15
any help plz ?

---

### Post by anejo on 2012-04-19
Does this help...?
To activate "click on tap" for your touchpad
```
sudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf
```and replace the content of the file with the following:
```
Section "InputClass"
Identifier "touchpad catchall"
Driver "synaptics"
MatchIsTouchpad "on"
Option "TapButton1" "1"
Option "VertEdgeScroll" "1"
EndSection
```

---

### Post by Meneth on 2012-04-20
I had this same problem on xubuntu 11.10. I fixed it by installing and running gpointing-device-settings. It must be run from terminal; no icon is installed.

---

