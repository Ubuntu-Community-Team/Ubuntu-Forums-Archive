---
title: "Keyboard stopped working for one user"
date: 2010-05-30
forum: General Help
---

### Post by jbm222 on 2010-05-30
I'm running 10.04, typically using the default gnome session.   

I locked my screen overnight, and when I came back the keyboard wasn't working.  Before anyone asks, yes it is still plugged in.

Here's where it gets weird.  I logged out using the mouse, and switched to another user on the system, and it works fine.  I have keyboard input on the gdm log on screen and for other users.   

I've tried about every possible combination of logging on/off and rebooting and nothing seems to work.

Is this an Xorg thing or a gnome thing?   Any ideas what to do from here?   

I can still get to a terminal through another user and then "su" to my user so I can run "sudo" commands.  So in other words, no need to bring in a live CD or a clean install at this point, but I don't really know where to start with this one.


UPDATE:   I switched session types to LXDE, and the keyboard DOES work for my user.  However, when going back to gnome it still doesn't work.    I guess that seems to point towards it being a gnome thing, not Xorg.

---

### Post by jbm222 on 2010-05-30
Another update:

The keyboard that doesn't work is a PS-2 keyboard.   I found a USB keyboard and plugged it in and it works.  The PS-2 keyboard still does not.

As an interesting side note, when I hit the numlock key on the usb keyboard, it toggles the light on BOTH keyboards!

---

### Post by jbm222 on 2010-05-30
Ok, apparently "slow keys" was active.   Whether or not I did this with realizing, I'm not sure.   But I did discover something I would call a legitimate bug:  

When you hold "shift" for 8 seconds, a dialog shows up asking if you want to activate slow keys.    There are 4 buttons on this dialog:  "Activate", "Dont Activate", "OK", and "Cancel".   3 of the 4 buttons activate it (both ok and cancel).   There only needs to be 2 options: activate, don't activate.   If for some reason there has to be an ok/cancel, OK should activate and cancel should not.

---

