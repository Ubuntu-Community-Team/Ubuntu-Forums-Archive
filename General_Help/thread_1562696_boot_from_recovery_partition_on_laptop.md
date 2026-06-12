---
title: "boot from recovery partition on laptop?"
date: 2010-08-28
forum: General Help
---

### Post by D3mon_Spawn on 2010-08-28
Hey all. I have a lenovo x100e laptop duel booting windows 7 and ubuntu 10.04. I'm using the GRUB bootloader and seem to have trouble trying to boot into the recovery partition that came with my laptop. I want to wipe my HDD clean by just having a fresh install of the factory OS that came with my computer from purchase, by using the recovery partition. When I interrupt the boot sequence from startup and press F11 it takes me to GRUB instead of booting the recovery partition. Am I doing something wrong? Or is there another way to do this?

---

### Post by Ibidem on 2010-12-05
Probably F11 needs a specific bootloader.
I'd try getting Grub to boot the recovery partition in that place, but I've been too long away from grub2.
In grub1, it's something like this at a grub prompt:
>makeactive (hd0,2)
>rootnoverify (hd0,2)
>chainloader +1
>boot

---

