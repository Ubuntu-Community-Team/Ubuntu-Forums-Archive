---
title: "Boot from Ubuntu on USB Drive with 2 Partitions?"
date: 2012-07-26
forum: General Help
---

### Post by Rytron on 2012-07-26
Hi.

Can I partition a pen drive in 2 parts and boot from GNU/Linux on partition 2 with regular files in NTSF partition 1?

Or would it make a difference if I put GNU/Linux on partition 1 and have regular files on partition 2 with NTFS?

---

### Post by C.S.Cameron on 2012-07-26
Windows will only see the first partition on a flash drive so put Ubuntu on partition 2.
Partition 2 should be FAT32 if you are doing a persistent install, (with usb-creator or UNetbootin), Use ext3 or ext4 if you are doing a full install.

---

### Post by Rytron on 2012-07-27
> **C.S.Cameron said:**
> Windows will only see the first partition on a flash drive so put Ubuntu on partition 2.
Partition 2 should be FAT32 if you are doing a persistent install, (with usb-creator or UNetbootin), Use ext3 or ext4 if you are doing a full install.

Hi C.S.Cameron.

Thanks for the tips.

What is the difference between a persistent install and a full install? Both save files to the Pen Drive right?

---

### Post by oldfred on 2012-07-27
Not to steal his thunder.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have a full install of Ubuntu in a 8GB partition with another 8GB for data on a 16GB flash. More for testing, but the larger apps are a bit slow loading but its functional. Once in memory everything runs well. A lighterweight version may load the lightweight apps a bit faster.

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

I also have a Windows repairUSB. It was a 2GB flash and used so little I wanted to use the rest. I shrank the FAT32 partition and put several LInux repair ISOs on the second partition and used grub2 to boot everything.

---

### Post by C.S.Cameron on 2012-07-27
Thanks OldFred.
Amjjawad's tutorial is great and still fairly valid for a Full install of 12.04.
For a persistent install there is Startup Disk Creator, (from the Live CD), UNetbootin and Universal, all offer a persistent install.
Iso's on USB can be booted using grub2, (MultiBootUSB).

---

### Post by Rytron on 2012-07-28
Cheers to you oldfred.

---

