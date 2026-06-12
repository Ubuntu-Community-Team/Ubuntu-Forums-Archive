---
title: "GNU GRUB loader question."
date: 2010-09-04
forum: General Help
---

### Post by plukpluk on 2010-09-04
I installed ubuntu netbook edition 10.04 for the first time and im dual booting it with windows 7 starter. Im confused as to what loader to choose to boot to ubuntu and windows 7 starter, when i turn on my netbook i get this options.. 
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)

so.. which one would be the best to boot ubuntu and windows 7 starter? why is there a vista loader in there..?

---

### Post by bobpress on 2010-09-04
Ubuntu, with Linux 2.6.32-24-generic is your newest Ubuntu kernel, the others are recovery and older kernels.

I would have to guess about the Windows entries.  The Windows 7 bootloader is  on *probably* on /dev/sda1 - this is the one you would select to run Windows 7.  Your actual Windows 7 files are *probably* located on sd2 .   It looks like your netbook came with a recovery partition, which would be on sda3.  The entries for sda2 and sda3 are there since there are Windows system files on those partitions.  If you used the entry for sda2, probably your computer would not boot and using the entry for sd3 would put you in the Windows recovery mode and could potentially remove the grub boot loader.

---

### Post by plukpluk on 2010-09-04
> **bobpress said:**
> Ubuntu, with Linux 2.6.32-24-generic is your newest Ubuntu kernel, the others are recovery and older kernels.

I would have to guess about the Windows entries.  The Windows 7 bootloader is  on *probably* on /dev/sda1 - this is the one you would select to run Windows 7.  Your actual Windows 7 files are *probably* located on sd2 .   It looks like your netbook came with a recovery partition, which would be on sda3.  The entries for sda2 and sda3 are there since there are Windows system files on those partitions.  If you used the entry for sda2, probably your computer would not boot and using the entry for sd3 would put you in the Windows recovery mode and could potentially remove the grub boot loader.Yeah you're right about the windows loaders because when i tested sd3 it took me to a system recovery. thanks :D

---

