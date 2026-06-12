---
title: "Graphics problem, it's driving me nuts!"
date: 2006-04-07
forum: General Help
---

### Post by MrChips on 2006-04-07
Games, screensavers, or anything that has openGL apps is stuttering in 1-2 second cycles.  I have posted this problem before but to no avail...so I have checked for background processes, drivers, everything.  I can't figure it out and it really blows the fine visual effects of this OS.

Gaming is impossible and it has diminished the effect of the really cool screensavers that Ubuntu/Linux has.  PLEASE HELP!!!

---

### Post by taurus on 2006-04-07
First thing first.  What is your video card and have you installed the driver for it???

---

### Post by MrChips on 2006-04-07
Nvidia Geforce 6200-all drivers installed.

I have not had this problem until just recently.  The only thing I can coincide with this is running automatix.

---

### Post by Huffers on 2006-04-08
the driver may be installed, but are you using it?

have a look in

/etc/X11/xorg.conf

(back it up first though)
there should be a section in it called

Section "Device"

you'll probably have to change the 'Driver' bit there, then reboot. If X doesn't start then revert what you did and reboot ;-)

also, what happens when you try running "fgl_glxgears"? If it just crashes you're not using your 3d drivers, if it runs fast, you probably are.

---

### Post by MrChips on 2006-04-09
Yes the driver is installed and working.:)  But still having the 1-2 sec hang in performance.

When I first installed I have had no problems with it doing this.  Like I said, this has only happened **after** I have run Automatix or tried to installed a DVD player.

I may just have to reinstall Ubuntu and be more careful of what I actually install.

---

