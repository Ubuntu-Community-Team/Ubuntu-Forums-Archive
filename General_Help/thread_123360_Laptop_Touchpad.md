---
title: "Laptop Touchpad"
date: 2006-01-29
forum: General Help
---

### Post by leetcharmer on 2006-01-29
Hi, is there a way to turn off clicking via the toucpad?  I just want to use it for moving the mouse and click with the real buttons.  Thanks!

---

### Post by tekwarren on 2006-01-29
I second this request! I don't like the touch/tap in windows and usually have it off it would be nice to know how to do it in Ubuntu also.

---

### Post by evs on 2006-01-29
If you use KDE you can install KSynaptics which will give you some different options (including the clicking and an option to turn off clicking only when you are typing).  It would be located in the Control Center under peripherals.  I doubt this would work with Gnome and I don't know if there is an equivalent.

EDIT:  I just looked into this a bit further.  It appears that there is a bug in the Breezy package of ksynaptics so the changes won't get applied, but there is a Qsynaptics package that works.  In your /etc/X11/xorg.conf file, under the Section "InputDevice" for the touchpad, add the following line:  
```
Option    "SHMConfig"         "1"
```
and restart X.

For example, that section of my xorg.conf looks like this:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "SHMConfig"             "1"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection
```
I launched qsynaptics from a terminal cuz I couldn't find it in the menu anywhere.

---

### Post by leetcharmer on 2006-01-29
I'm in gnome :D

---

### Post by evs on 2006-01-29
[QUOTE=leetcharmer]I'm in gnome :D[/QUOTE]
I just updated my post for qsynaptics instead, and I just tried it in Gnome and it works.  Give that a try and I hope it helps.

---

### Post by leetcharmer on 2006-01-30
thanks a lot!

---

### Post by leetcharmer on 2006-01-30
qsynaptics works great ... except, it doesn't really save the options.

When I reboot, the double tap is on again, and I have to run qsynaptics after every reboot.  Any ideas on how to have the options saved perminantly?

---

### Post by mrjyg on 2006-11-10
I don't use additional package but just a couple of entries in /etc/X11/xorg.conf's Synaptics InputDevice section:

Option "HorizSchollDelta" "0"
Option "MaxTapTime" "0"

The first option is to prevent scrolling / paging when sliding finger at the edge.

The second option is to disable tap.

You can find more synaptics driver options by 'man synaptics'.

No need to load yet another app.

---

