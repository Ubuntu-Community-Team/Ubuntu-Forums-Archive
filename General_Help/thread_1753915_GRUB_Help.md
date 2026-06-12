---
title: "GRUB Help"
date: 2011-05-09
forum: General Help
---

### Post by ComradeSlice on 2011-05-09
I know this isn't a forum for GRUB but I wanted to hear from people using GRUB with Ubuntu.

I'm trying to make a bootable USB flash drive. It's all good until I try to use the GRUB console to configure the flash drive.

> 
> root (sdb1,1)
will return

> 
Error 23: Error while parsing number
I used mkfs to create the device and every single possible fs allowed by GRUB. Here is exactly what I did:

> 
mkfs.msdos /dev/sdb1
mount /dev/sdb1 /mnt/sdb1
cd /mnt/sdb1
mkdir boot
mkdir boot/grub
cd boot/grub
cp /usr/lib/grub/i386-pc/stage1 .
cp /usr/lib/grub/i386-pc/stage2 .
cp /usr/lib/grub/i386-pc/fat_stage1_5 .
grub
> root (sdb1,1)
Thanks in advance!

---

### Post by ComradeSlice on 2011-05-09
(bump)

---

### Post by drs305 on 2011-05-09
The instructions you are using appear to be for Grub legacy (0.97). Do you have a specific reason for using it instead of Grub 2?

One reason you may not have received a prompt reply is that our knowledge of Grub legacy is rapidly dimming.

If you do a search for "grub 2 bootable flash drive" you will find plenty of guidance.

And don't worry about asking Grub questions on these forums. There are literally hundreds of thousands of Grub thread views on the topic.

---

### Post by ComradeSlice on 2011-05-09
I thought the grub package was the latest using apt-get. What is the name of the package for the latest GRUB and what's the proper way to "bless" devices using it? I would check myself but their wiki seems to be offline at the moment.

---

### Post by drs305 on 2011-05-09
You can check which version of Grub you are using with:
```
grub-install -v
```
All the supported Desktop versions of Ubuntu will be using Grub 2 by default by the middle of next month (when Hardy reaches EOL). The version number varies from 1.97~beta to 1.99RC.

The package is called "grub-pc". Grub legacy is "grub".

If your system is still using Grub legacy and you are happy with it there probably isn't a drastic need to upgrade until you upgrade your OS. There are quite a few improvements with Grub 2 but it takes some getting used to.

---

### Post by ComradeSlice on 2011-05-09
Thank you very much! GRUB 2 is perfect. You've been a great help :D

---

