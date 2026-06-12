---
title: "Blank unresponsive screen when trying to suspend"
date: 2010-08-29
forum: General Help
---

### Post by jxtreme on 2010-08-29
When I try to suspend my laptop, the screen goes black but the laptop doesn't actually suspend. (No pulsing power button) If I open it back up the backlight will come on and I can change the brightness, but that's it. I'm using the proprietary fgrlx drivers, version 10.8 from the ati website. aticonfig --initial or aticonfig --initial -f does not help. This happens even in failsafe graphics mode, so not an fgrlx problem. Before this happened it was taking a very long time to resume from suspend and one time it tried to hibernate it didn't have enough swap. Kernel version is 2.6.32-24-generic, 64-bit. This happens on -23 also. I'm running lucid.

EDIT: Had an SD card in the slot. Works fine now. That should really be fixed...

---

