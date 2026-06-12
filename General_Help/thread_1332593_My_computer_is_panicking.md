---
title: "My computer is panicking???"
date: 2009-11-20
forum: General Help
---

### Post by lowvoice on 2009-11-20
Hi I recently upgraded my SD ram card (I know retro right?) and now my computer won't boot and it kept coming up with BUG: Int 14: CR2 followed by a lot of other gibberish, so I tried installing the latest version of ubuntu from the live cd (was using the previous version) and my computer boots to the CD however when I try to proceed with the install it comes up with kernel panic-not syncing: out of memory and no killable processes. If anyone can tell me how to restore my computer to how it was wrking before I install the RAM card that would be great, I tried removing the ram card but that didn't work alternatively if you could help me install the new version that would also be great or if you could tell me whats wrong with my computer at least then I'll know and that'll be an improvement. I do wish to regain the use of my computer as I need it for University work. Thanks

---

### Post by P4man on 2009-11-20
What computer is this? What does the SD card have to do with anything?
I also dont understand what happens with the livecd, are you saying you can boot the live cd and it works fine, but after installing it you get that kernel panic?

---

### Post by Confusatron on 2009-11-20
Sounds like bad RAM - did you try it with *only *the new stick ("RAM card")? If you run memtest at boot (either from grub or off the ubuntu CD), that will help diagnose if it is RAM.

---

### Post by P4man on 2009-11-20
BTW a quick google on Int 14: CR2 seems to suggest a wrong kernel, like 64 bit kernel on a 32 bit machine, or a 686 kernel on a old PC or something like a VIA Epia which needs a different kernel (386 optimized).

---

### Post by lowvoice on 2009-11-22
Ah success it was a dodgy ram card just like you suggested. I removed it and put an old one in and it booted fine to my hard drive. Thought I would have been fine with Kingston but at least it works now. Thank you :):):):):)

---

