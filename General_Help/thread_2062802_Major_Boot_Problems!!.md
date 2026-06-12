---
title: "Major Boot Problems!!"
date: 2012-09-25
forum: General Help
---

### Post by sl135 on 2012-09-25
I recently tried to change back from the Windows Boot loader to Grub, but in doing so i managed to completely mess up somehow! :confused:

I have my computer on dual boot using Ubuntu and Windows 7.

Now when i try to boot neither comes up!  

I have tried using the Boot-Repair tool but the problem persists.

At the end of Boot Repair I am given this URL which  [http://paste.ubuntu.com/1227481/](http://paste.ubuntu.com/1227481/) 

Also, it gave this message:
"The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)".

I tried to create such a partition but only 4 primary partitions are permitted!

Help is very much needed at this moment in time. 

Thanks in advance.

---

### Post by oldfred on 2012-09-25
Welcome to the forums.

There seems to be a bug in grub2 with larger / (root) partitions or partitions located higher on the drive. There used to be a BIOS issue on old computers with IDE interfaces that they would not boot beyond 137GB. But now grub2 seems to have a similar issue with newer computers.

You can check to see if your BIOS is set for IDE mode for drives. It should be LBA, large or AHCI. That may help.

You can try shrinking your / (root) partition just to see if having grub & boot files closer together works even though they are higher on drive. 

If none of that works. Do you use the Dell Utility Partition? I do not know what it is used for. Many vendors just have a few utilities that really do not do much, some have special links to function keys on system. Not sure if Dell Utilities would still work but you could move them to a new fAT16 partition at the end of the drive and reformat sda1 to ext2. Then make sda1 the Linux boot partition.

---

### Post by YannBuntu on 2012-09-27
Welcome among us :)

> **sl135 said:**
> At the end of Boot Repair I am given this URL which  [http://paste.ubuntu.com/1227481/](http://paste.ubuntu.com/1227481/) 

1) First: from liveCD/USB, run Boot-Repair --> Advanced options --> tick the "Restore MBR" option --> go to the "MBR options" tab --> select "Partition booted by the MBR: sda3" --> Apply. Reboot the PC, you should get direct access to Windows. If not, stop here and tell us.

2) Backup your documents on an external disk (or DVDs)

3) Then use Gparted to delete the sda2 partition (15.7GB). Format it in EXT4. Follow this tutorial to make it a /boot partition for Ubuntu: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) Tell us the URL provided by Boot-Repair. Reboot the PC without any liveCD/USB, and tell us what you observe.

---

