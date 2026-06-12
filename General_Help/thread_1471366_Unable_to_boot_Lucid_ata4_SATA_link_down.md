---
title: "Unable to boot Lucid: ata4: SATA link down"
date: 2010-05-03
forum: General Help
---

### Post by asuastrophysics on 2010-05-03
Hi guys,

After correcting my grub bootloader problem earlier, I seem to be running into a different problem. I am unable to boot Lucid Lynx, either through recovery mode or normal boot. In recovery mode, I get the following message:
```
ata4: SATA link down
```
It then goes on to tell me, after a long wait, that it's unable to start TTY, and shows a (initramfs) prompt.

Does anyone know what I can do to fix this? 
BTW, thanks community for being so helpful to me the last few days!:popcorn:
:D

---

### Post by asuastrophysics on 2010-05-03
Ok, I noticed something strange when I went to the grub2 command line. 
```
grub> root
(hd0,1): Filesystem is ext2.
```
Which is odd, because it's definitely ext3. I think I need to do more work to try and get rid of GRUB2. I attempted to remove it by following a guide, but it hasn't seemed to work

UPDATE: the ext2 thing has nothing to do with it apparently; this is a feature of GRUB and it's normal. But I still can't use my computer. I will post the output of my boot log shortly.

---

