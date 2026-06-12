---
title: "dpkg broken: hangs on unpacking"
date: 2011-08-14
forum: General Help
---

### Post by d3v1150m471c on 2011-08-14
I can't install or uninstall packages using apt nor synaptic. when i try to install something, dpkg hangs on the unpacking stage. it will also tell me that file lists are missing from packages when i try to uninstall them. or it will tell me it cannot find an archive for various packages. dpkg --configure -a # does not work, btw.

---

### Post by d3v1150m471c on 2011-08-14
i did some more digging to find the source of the problem and strangely enough it was because df couldn't detect my usb drive...not entirely sure how that occurred but got it fixed lol.

---

