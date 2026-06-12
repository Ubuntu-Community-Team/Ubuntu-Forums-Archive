---
title: "resolution forced to 800x600 upon reboot, wine related"
date: 2010-06-20
forum: General Help
---

### Post by ubdime on 2010-06-20
So a few weeks back, friend of mine ran into some issues while playing wow on wine. When trying to take a screenshot, it messed up the resolution and video froze.

Upon rebooting, resolution is set to 800x600. I've tried many ways to try to set this, including xrandr in .xprofile, in /etc/init.d. And reconfiguring X.

I've completely purged all nvidia packages, and reinstalled. But the issue persists.

A parallel issue exists where some wine programs (like utorrent) only run in a box that's 800x600 max whereas wow will still run fullscreen.

This can be fixed by removing .wine/ folder and using default (although we use a backed up .wine/ since it includes changes to make MS Office work).

But when things get updated, such as when update-manager updated the version of wine, the 800x600 box limit came back.

This is likely one of the most bizarre issues I've seen and I'm pretty close to just wiping this computer and restarting. Unless anyone has any ideas? Thanks in advance.

---

