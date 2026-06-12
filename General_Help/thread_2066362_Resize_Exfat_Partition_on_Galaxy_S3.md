---
title: "Resize Exfat Partition on Galaxy S3?"
date: 2012-10-04
forum: General Help
---

### Post by cbanakis on 2012-10-04
Not sure if this can be done, but it would be amazing if I can do it.

I'm trying to edit the partitions on the sd card in my Galaxy S3.

The plan is to have a boot-able partition, for the purpose of loading iso's.

The end result being...

64GB SD card.
2 Partitions.
50GB For Phone
14GB For ISO's

The plan being, for me to be able to plug my phone into any computer, boot to the SD card, select an ISO, and either live boot, or install.

Can this be done?

I tried gparted, but it cannot edit exfat partitions.

The SD card is backed up, so I'm fine with erasing it.


Also, I do have SGS3 Easy UMS installed on the phone.
So when I plug the phone into a usb port, the computer has direct and sole access to the SD card.  So in theory, this should work.

---

### Post by cbanakis on 2012-10-04
I found out that my phone reads FAT32.

Formatted to FAT32,  and managed to make it a bootable drive without partitioning with GRUB2.

Now on to phase 2.

---

