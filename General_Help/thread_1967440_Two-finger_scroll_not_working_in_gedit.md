---
title: "Two-finger scroll not working in gedit"
date: 2012-04-28
forum: General Help
---

### Post by johnitsa on 2012-04-28
Starting yesterday the two-finger scroll on my laptop seems to be acting up. It works perfectly in almost everything, except gedit and nautilus. I wasn't able to find any reference to this issue, albeit searching for a few hours.

Has anybody experienced this issue? Any ideas what could be the cause?

I'm running Ubuntu 12.04 (upgraded from 11.10) on an Asus U36SD with a Synaptics touchpad.

---

### Post by johnitsa on 2012-04-28
After looking around, I sumbled on this bug report [https://bugs.launchpad.net/bugs/982771](https://bugs.launchpad.net/bugs/982771)

The issue is now fixed. I upgraded the xserver-xorg-input-synaptics package from precise-proposed. Check comment #6 on how to enable testing with precise-proposed.

---

