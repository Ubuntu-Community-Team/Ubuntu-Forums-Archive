---
title: "Dual Booting"
date: 2006-05-01
forum: General Help
---

### Post by chris062689 on 2006-05-01
I have recently decided to duel boot Windows XP and Kubuntu.

I was thinking, is there a way with QEMU, to do the following...

I boot up my computer..
GRUB PROMPT: Asking if I want to choose from XP Or Kubuntu
Boot up Windows XP, and then run QEMU, using the hard-drive in QEMU, come up with the GRUB Bootloader rerouting to Kubuntu (the same one that is on my other partition)

Basicly; can I run a Dual Boot with XP and Kubuntu, and still access Kubuntu WITHIN XP with QEmu?

Would this make kubuntu more likely to be affected by windows viruses?

---

### Post by aysiu on 2006-05-01
I may be wrong, but I don't think Qemu can emulate based off a hard drive or partition. You may need something like VMWare.

Keep in mind, too, that emulation of one operating system *within* another operating system will be extremely slow unless you have over 1 GB of RAM.

Your best bet, instead of dual-booting, would be to get a super-cheap or free computer (maybe one that a friend or relative thinks is too old to be useful) and install Kubuntu on that. Then, set up desktop sharing and use TightVNC on Windows to control the Kubuntu computer from within Windows.

---

