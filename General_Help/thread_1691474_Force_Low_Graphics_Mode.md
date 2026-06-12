---
title: "Force Low Graphics Mode?"
date: 2011-02-19
forum: General Help
---

### Post by chessnerd on 2011-02-19
**Question:** How do I force Ubuntu to always boot into low graphics mode, without getting a selection dialog every time?

**Long-winded explanation:** I'm running Ubuntu 10.04 on an old desktop that has an equally old nVidia TNT2 card in it. The proprietary drivers are not supported since Ubuntu 9.10 and the open-source ones leave a lot to be desired. 

In my messing around with fixing this, I discovered that low graphics mode works *better* than the regular graphics mode. It is less buggy and supports the same max resolution. Because of this, I would like to have it always boot up that way (without the annoying dialog).

I figured a quick Google search would work, but there seems to be only answers of how to get *out* of low graphics mode and how to enter it as a one-time thing (with the dialog), but not how to enter it permanently.

Any thoughts?

---

### Post by jerrrys on 2011-02-21
i took a look around too, and your right.  maybe you could trade boxes with one of those guys :) or maybe you can edit xorg to do this.  myself, i have not tried this

---

### Post by BeerGarage on 2012-02-18
This works to force low graphics mode:

I copied /etc/X11/xorg.conf.failsafe to xorg.conf

sudo cp /etc/X11/xorg.conf.failsafe xorg.conf

so the failsafe settings are used every startup.

---

