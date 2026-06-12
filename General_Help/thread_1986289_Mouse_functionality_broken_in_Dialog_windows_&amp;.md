---
title: "Mouse functionality broken in Dialog windows &amp; New windows."
date: 2012-05-24
forum: General Help
---

### Post by Advoc on 2012-05-24
This problem is difficult to describe exactly because it differs in behavior a bit across versions.

If I have a window open and it opens a dialog box, the dialog box is completely unresponsive to the mouse.  You can mouse over and nothing will highlight, and clicking does nothing.  All other windows / widgets / panels are also unresponsive.  It's as if the mouse will only interact with one window or panel at a time, and if something else opens up, the mouse will stop working.

I've seen several versions of this issue crop up over different forums, and here as well, and there seems to be little help available.  I'm hoping its because of the lack of information given by the bug reporters.

I've tested it in A handful 64 bit version of Ubuntu 12.04 and derivatives and its the same problem in all versions.  I would like to try it in some other distros to see if the problem persists, but for some reason none of the other LiveCD's seem to work.

The only version that seems to have a bit less of a hassle is Kubuntu.  In the Live CD there wasn't a single problem.  It worked no matter what, but after installation, the problem persists. (might be worth noting that when booting into the Kubuntu live CD, if you go straight to "install" then the problem is there, if you go to "try" first, and then "install" then the problem is fixed.)

The closest thing I've found is this bug report:
[http://tinyurl.com/ckwzrtc](http://tinyurl.com/ckwzrtc)

but my problem isn't quite the same.  I haven't used any of the special buttons on my keyboard.

The problem might be tied to my hardware.  I'm using a Microsoft wireless keyboard/mouse pair, without the mouse. and a Saitek RAT7 wired mouse.  Perhaps the trouble is the wireless receiver expects a mouse that I'm not using and the RAT7 is considered a 2nd mouse??

I'd really appreciate some help.  I haven't used Ubuntu since Karmic because of this problem, and I don't really know how to use any other distro of linux.

Live CD's tested:
Ubuntu 12.04 64-bit
Ubuntu 12.04 32-bit
Kubuntu 12.04 64-bit
Ubuntu Studio 12.04 64-Bit
Linux Mint 13 - "Mate"

---

### Post by Advoc on 2012-05-29
Issue is solved (sort of)

Using the keyboard and terminal I opened Muon Package manager and installed:

xserver-xorg-input-evdev-dev

Then marked for re-installation

xserver-xorg-input-evdev

After a logoff and re-logging in, the problem was fixed.

However, upon reboot, the problem persists.  I must log in, log out, then log back in again before the problem goes away every time I start my computer now.

I'll keep the thread as unsolved until this last issue is resolved, any ideas would be welcome.  I'm amazed nobody has had any input.

---

