---
title: "mouse goes lower than bottom of screen"
date: 2011-11-10
forum: General Help
---

### Post by Quan-Time on 2011-11-10
```

Linux Shim 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Gnome, 11.10 "default" install.  Most things working great.  I have a 1600x900 Nvidia (current driver) laptop screen.  When i move the mouse to left, right and top of the screen, touching the boarder, the mouse pointer works as normal.

When i go to the bottom of the screen (laptop touchpad, i also use "classic" look with taskbar down the bottom), the mouse can go LOWER than the screen.  Instead of stopping at the bottom of the screen, it can go about 1" lower.  I cant work out why its doing it, or how to stop it.  Its persistent every boot, and cant fix it.

Anyone heard of this, or experienced it, or better yet, know how to stop it ?

I sometimes use twin view with a 1280x1024 monitor.  Could this be how it all came about ?

---

### Post by notgary on 2011-11-10
If you're using multiple displays of different resolutions, then the smaller display will actually have an *effective* resolution matching the larger one, even though the actuall usable resolution is correct. One of the goals of the 12.04 release cycle is to [improve support for multiple monitors]("http://www.omgubuntu.co.uk/2011/11/multi-monitor-support-to-improve-in-ubuntu-12-04-video/"). You may want to drop by the [Ubuntu Desktop mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-desktop") and give them a heads up that this is an issue you'd like to see fixed.

---

