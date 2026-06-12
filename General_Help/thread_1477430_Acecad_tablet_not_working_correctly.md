---
title: "Acecad tablet not working correctly"
date: 2010-05-08
forum: General Help
---

### Post by maturin on 2010-05-08
I've had no luck getting an Acecad tablet working correctly with Lucid (actually using Xubuntu).  

The problem: once you use the pen to click on the pad (e.g., to draw something), then lift the pen (unclick??), the tablet no longer tracks the movement of the pen until the next "click".  This is very frustrating since one doesn't know exactly where the pen is on the screen until one clicks again.  

Have tried numerous things, including installing an older version of the acecad driver (xserver-xorg-input-acecad).  

The only other thread I've found is:

[http://swiss.ubuntuforums.org/showthread.php?t=1342034](http://swiss.ubuntuforums.org/showthread.php?t=1342034)

but none of the suggestions there seem to work.

Incidentally, this worked just fine under hardy.

Thanks ahead of time for any help.

---

### Post by Favux on 2010-05-08
Hi maturin,

Did you save your Hardy xorg.conf?  We may be able to use it in the Lucid xorg.conf or translate it into an acecad.conf in /usr/lib/X11/xorg.conf.d/.  You might want to check in that directory to see if you already have one.  Also try /etc/X11//xorg.conf.d/.

---

### Post by maturin on 2010-05-09
Yes, I had saved the old configuration, and had even copied the relevant section from the old xorg.conf file.  Or so I thought.

After your reply, I tried again and copied the entire xorg.conf from hardy, and now it's working fine.  Seems strange - I would have thought all that was needed was the section describing the acecad driver.  I wish I really knew what's going on under the hood, but the important thing is it's working now.

Thanks.

(Possibly off topic - you have a good link describing what xorg.conf.d does?  Haven't used it before).

---

### Post by Favux on 2010-05-09
Hi maturin,

Good deal, you're setup!  :)

I doubt you need the whole Hardy xorg.conf.

I don't have good links for .conf yet.  That's part of the problem, it's new enough that the documentation isn't exactly thick on the ground.  This Fedora wiki is probably the best:  [https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)

---

### Post by maturin on 2010-05-15
Well, after a hiatus of a week or so, I've managed to discover another problem.

First it does work correctly if I don't change the resolution of the screen.  The problem is, I use the tablet on a laptop which I often use for lectures in a University setting.  The upshot is that the screen resolution often changes due to the external monitor/projector.

Once I change the resolution of the screen, the tablet exhibits quite strange behavior.  Specifically, in a graphics program, when I set the pen down (i.e. click), the pointer jumps and a line is drawn from the original point where I set the pen down (indicated by the mouse/pen cursor before "clicking" with the pen) to the new point (where the pointer jumps to after "clicking" with the pen).  Obviously this makes "writing" (or drawing, for that matter) on the tablet useless.

I've done some initial investigation and have discovered two things:

1) These "lines" get longer the lower or higher I set the resolution.  This seems to indicate to me that something in the ACECAD tablet driver is not picking up the new resolution (at least for pen clicks).  It seems "stuck" at the original resolution.  Resetting to the original resolution restores correct function.  This is true with or without an external monitor attached.

2) If I have an external screen plugged in when starting X, it will work correctly at whatever the highest resolution supported by both the laptop screen and the external screen (e.g., 1024 x 768, or whatever).  Trying to change the resolution to either a lower commonly supported resolution or a higher resolution supported, say, on the external screen only, results in the same problem.

This is probably not a real urgent issue (for me) since I think I can make it work well enough, but it's not ideal behavior.  It'd be nice to have the flexibility to adapt to whatever the best that the external monitor/projector can do.

Anyone have any advice on this, or if not, can anyone suggest where a bug report might be filed?

Thanks.

---

