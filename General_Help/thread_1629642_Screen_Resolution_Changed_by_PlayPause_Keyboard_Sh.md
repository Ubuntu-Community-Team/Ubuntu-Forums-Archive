---
title: "Screen Resolution Changed by Play/Pause Keyboard Shortcut?"
date: 2010-11-24
forum: General Help
---

### Post by floborg on 2010-11-24
I've had "Play (or play/pause)" mapped to Mod4+p (Windows key + p) for a few Ubuntu releases, but, today, it is causing my screen resolution to increase as well as pausing Rhythmbox.  Using Windows+p a second time causes the screen resolution to return to normal.

I can't find any conflicting keybindings in Gnome's Keyboard Shortcuts Prefences nor in the CompizConfig Settings Manager.

What happened?  I noticed this after applying today's updates (using Maverick + Gnome + Compiz), which included a kernel update.

---

### Post by floborg on 2010-11-24
So, I booted into the older 2.6.35-22 kernel (as opposed to the updated -35 kernel), and the problem was still present.

I also tried the liveCD environment, and was not able to reproduce the problem.

---

### Post by floborg on 2010-11-25
Ok, this was caused by an Ubuntu update to gnome-settings-daemon.  They pushed a new version out with what seems like minimal testing to fix a problem that appears to be specific to laptops.  Now, it looks like they have broken the Mod4+p shortcut for everyone else.  See this bug:

[Bug #539477]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539477")

I downgraded to version 2.32.0-0ubuntu2, and, guess what!  The problem went away after a restart.

---

