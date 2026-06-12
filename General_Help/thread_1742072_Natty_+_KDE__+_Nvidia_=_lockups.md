---
title: "Natty + KDE  + Nvidia = lockups"
date: 2011-04-28
forum: General Help
---

### Post by lykwydchykyn on 2011-04-28
Since upgrading my system to Natty, I'm having nasty GPU lockups all the time.  One I can consistently reproduce is resizing a konsole window.

The same bug has been seen in Arch Linux (see [Here](https://bbs.archlinux.org/viewtopic.php?id=116544&p=1)), and seems to be either a problem with the new xserver or the new nvidia (proprietary) drivers.

Not much you can do about it, but if you're using KDE with Nvidia, I'd suggest sticking with Maverick or Lucid for the time being.

FWIW:  My card is a geForce 8600 GS dual-head.  Using the proprietary driver.

EDIT: Launchpad bug for this one, if you want to add your name to it:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/761575](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/761575)

---

### Post by wizard10000 on 2011-04-28
> **lykwydchykyn said:**
> Since upgrading my system to Natty, I'm having nasty GPU lockups all the time.  One I can consistently reproduce is resizing a konsole window.

The same bug has been seen in Arch Linux (see [Here](https://bbs.archlinux.org/viewtopic.php?id=116544&p=1)), and seems to be either a problem with the new xserver or the new nvidia (proprietary) drivers.

Not much you can do about it, but if you're using KDE with Nvidia, I'd suggest sticking with Maverick or Lucid for the time being.

FWIW:  My card is a geForce 8600 GS dual-head.  Using the proprietary driver.

EDIT: Launchpad bug for this one, if you want to add your name to it:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/761575](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/761575)

Must be hardware-specific.  I'm running Kubuntu 11.04 64-bit with proprietary drivers and no issues.  My card's a GF 9500GT

Strange.

---

### Post by lykwydchykyn on 2011-04-28
> **wizard10000 said:**
> Must be hardware-specific.  I'm running Kubuntu 11.04 64-bit with proprietary drivers and no issues.  My card's a GF 9500GT

Strange.

That wouldn't surprise me, but from what I've been reading, a lot of nvidia hardware is affected.

---

### Post by wizard10000 on 2011-04-28
> **lykwydchykyn said:**
> That wouldn't surprise me, but from what I've been reading, a lot of nvidia hardware is affected.

I've heard that too.  Wonder if anybody knows which models work and which don't?

---

### Post by lpetersen on 2011-05-01
Happens here too on the

```
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)
```

in my Sony Vaio F12.

Bad thing is, the nouveau driver isn't really an alternative either, since it also suffers from the infamous lockups reported everywhere on the forums ... :(

---

### Post by lykwydchykyn on 2011-05-01
> **lpetersen said:**
> Happens here too on the

```
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)
```

in my Sony Vaio F12.

Bad thing is, the nouveau driver isn't really an alternative either, since it also suffers from the infamous lockups reported everywhere on the forums ... :(

Yeah, same here; the nouveau driver made a mess of my desktop, and I couldn't get dual monitors to behave.  Guess we are at the mercy of Nvidia still...

---

### Post by Kokopelli on 2011-05-10
I have noticed that in my case the lockups mostly (perhaps only) occur when resizing windows in a multimonitor configuration.  Maximizing and restoring work fine, but when I try and manually resize a window the xorg process becomes locked and starts consuming 100% of 1 core.  There is nothing in xorg.log when it locks though I have not checked farther back.

I am on Kubuntu Natty with a GeForce GT 320M gpu.

If others are willing can you try the following steps:

1) activate 2 monitors (if not your default configuration)
2) open multiple windows
3) attempt to manually resize the windows.

There are a number of variables I would like to explore now that I see that others are having similar problems, but it will have to wait till I get home.

To be thorough I would like to try and induce a lock state in:
a) single monitor without desktop effects
b) single monitor with desktop effects
c) twinview without desktop effects
d) twinview with desktop effects

and see what combinations have the most/least troubles.

EDIT: Just noticed this is from a week ago.  Have your problems been solved or is this still ongoing for you?

---

### Post by lykwydchykyn on 2011-05-10
It's not been solved, KDE 4.6.3 didn't fix it (though I didn't expect it to, since this is apparently and nvidia or xorg bug).

I do have dual monitors on the affected computer, but so far I've only noticed the problem on konsole windows (which I use often).  I tried a few different terminals, and it seems like any terminal that supports transparent backgrounds (whether or not you actually set the background transparent) crashes.  Xterm is unaffected.

---

### Post by lykwydchykyn on 2011-06-14
GOOD NEWS!

Looks like Nvidia has released a driver update which seems to address the issue (I hope):

[http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html)

I'm personally waiting until this hits a package repo, which will hopefully be very soon!

---

