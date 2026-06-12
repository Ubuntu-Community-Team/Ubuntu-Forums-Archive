---
title: "unity 3d not running"
date: 2011-12-22
forum: General Help
---

### Post by dougleduck on 2011-12-22
Hi,

I'm trying to get unity 3d running and my graphics cards working, currently only 2d works. The driver for my amd card is supposedly installed, but I get the following error when I try to run the 'AMD Catalyst Control Centre'.

[INDENT]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.[/INDENT]

Really I think even my internal card should be able to handle unity 3d.

Which is the best driver for my card (preferably one that can do graphics scaling and switching between the integrated intel card and my amd)?

Thanks for any help.

---

### Post by elliotn on 2011-12-22
its could be a mess up with the drivers, search for any nvidia related package and remove it, then restart and see, I hope it is it

---

### Post by dougleduck on 2011-12-22
The only package that might be nvidia related it xserver-xorg-video-nouveau, and its not clear if this is designed 'only' for nvidia graphics cards.

---

### Post by dougleduck on 2012-04-10
I managed to get my graphics card working by installing the drivers from amd manually.

Instructions [here]("I managed to get my graphics card working by installing the drivers from amd manually.  Instructions here.  I didn't have any problems, and the instructions were easy to follow.").

I didn't have any problems, and the instructions were easy to follow.

---

