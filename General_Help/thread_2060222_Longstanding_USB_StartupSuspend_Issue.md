---
title: "Longstanding USB Startup/Suspend Issue"
date: 2012-09-19
forum: General Help
---

### Post by alanwalterthomas on 2012-09-19
I have had this problem for *years* now.

Currently using 12.04.
Gigabyte 780GPM-DS2H Motherboard

When the ubuntu desktop appears after starting the computer, or after resuming from suspend, USB remains powered off for a few minutes. The keyboard always recovers first, the mouse a couple minutes later.

Are there any USB diagnostic tools that I might use to figure out what the problem is?

---

### Post by f8l_0e on 2012-09-19
There was a known bug in the SB700 southbridge regarding USB freezes.  It was patched back in kernel 2.6 bug  and the patch is still there in kernel 3.2.  Perhaps the patch fixes USB from freezing completely but effects how quickly it brings up the host controller?  If you have an open PCIe slot, I would just put a new USB2 or USB3 controller in.

---

