---
title: "Disable sound via software"
date: 2006-04-30
forum: General Help
---

### Post by Ribs on 2006-04-30
Is a clean/non-kludge-like way to make Ubuntu ignore/turn off my on-board sound card?

I recently got a PCI sound card to replace my on-board one, and I find that Ubuntu assigns whatever /dev/dsp* number it likes to either card when it boots (same with alsa as well). Turning off my on-board sound would cure this, however there is no way to do it via the BIOS screen. Can this be cleanly done in software?

I did think about just deleteing the module, but I figured this would be bad, especially as a kernel upgrade would just add it back in.

Cheers,
Ribs.

---

### Post by hollywoodb on 2006-04-30
You can prevent the modules from loading without deleting them... This method will keep constant through kernel upgrades and such as well.

[http://ubuntuforums.org/showthread.php?t=166624]("http://ubuntuforums.org/showthread.php?t=166624")

---

