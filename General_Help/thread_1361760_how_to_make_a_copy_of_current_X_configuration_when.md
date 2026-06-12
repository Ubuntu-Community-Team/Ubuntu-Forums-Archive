---
title: "how to make a copy of current X configuration when there is no xorg.conf?"
date: 2009-12-22
forum: General Help
---

### Post by simple simon on 2009-12-22
To solve my perpetual login problem ([http://ubuntuforums.org/showthread.php?t=1347584](http://ubuntuforums.org/showthread.php?t=1347584)) I need to start fiddling with my x settings.  However I would like to save my current settings in case I break them yet further.  But at the moment I have no xorg.conf as I understand karmic does not use one by default (but will if there is one available).

So how do I back up my current x settings?

In anticipation...

Simple.

---

### Post by pbrane on 2009-12-22
If you don't have a /etc/X11/xorg.conf then you don't need to back anything up. when you want to go back to default just delete the xorg.conf that you create. And you *may* have to run **sudo dpkg-reconfigure -phigh xserver-xorg** in a terminal.

---

