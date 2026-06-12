---
title: "Less advanced GRUB when writing ISO to USB?"
date: 2010-05-22
forum: General Help
---

### Post by directedition on 2010-05-22
I've rolled a custom version of the live CD, and everything's going great on it. I was asked to make it a bootable USB stick as well. This was simple enough by installing UltraISO on my Windows box and writing the ISO to a USB stick through the 'Bootable' menu. But for some reason it boots up to a slightly less-pretty version of GRUB.

That's all well and good, but now the language selection menu is gone. Is there any way to get that menu in the less-pretty GRUB? At the very least, is there a way to hard-code the language there so certain people have sticks with certain languages?

Thanks for any help!

---

### Post by directedition on 2010-05-23
Stupid me, it isn't GRUB. The boot loader for the CD is ISOLINUX, and the boot loader that gets put on the USB stick by UltraISO is Syslinux.

I've spent a while looking around, but I can't find a reliable doc on how to set the language of the system from a syslinux config file. I imagine that this must be possible. How would I do this?

---

