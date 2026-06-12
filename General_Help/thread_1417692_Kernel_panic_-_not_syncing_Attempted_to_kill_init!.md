---
title: "Kernel panic - not syncing: Attempted to kill init! error"
date: 2010-02-27
forum: General Help
---

### Post by GrfyGrumpyBear on 2010-02-27
Hello

I keep getting the Kernel panic - not syncing: Attempted to kill init! error on boot of my Fiesty (ancient, I know) installation, dual-booting with windows XP. The recovery console highlights the error as : kmap atomic +0x5c/0xz0 SS:ESP 0068df905df8.

It does not boot at all. 

Help!

---

### Post by quixote on 2010-02-28
Can you boot with a Feisty LiveCD and see whether the partition can be mounted?  If yes, and if it looks normal in nautilus, then the problem is just grub or, perhaps, the windows bootloader blowing up grub.  If nautilus can't see it, then there's a bigger problem. :(

---

