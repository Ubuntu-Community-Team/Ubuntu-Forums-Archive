---
title: "Maverick corrupts USB ?"
date: 2010-12-03
forum: General Help
---

### Post by aboud on 2010-12-03
after few unsuccessful attempt to mount external HDD on 64 Ubuntu, I turned to windows machine to find the drive was damaged, the same happened to USB flash after it was connected to the Maverick machine.  

anyone experienced something similar ?

---

### Post by efflandt on 2010-12-03
I have been using various versions of Ubuntu since 9.04 a week before 9.10 was released and have never had issues with USB flash or hard drives, unless I tried to erase a drive instead of partition when using Startup Disk Creator for USB flash.  And then it was just a matter of using gparted to recreate an msdos partition table and the FAT32 partition.

On USB hard drives (WD Passports) I have mixed FAT32 or NTFS and Linux partitions (ext3 or ext4) without any issues.  Except that "some" computers do not seem to be able to boot beyond a certain point on a large USB drive.

Make sure that you figure out which way is up and plug in the USB cable quickly (don't fiddle with it plugging it in), in which case it should automount.  And before disconnecting it either **Eject** or **Safely Remove Drive** (if not **umount** it from a shell) to make sure that it is flushed and finished writing before disconnecting it.

What does **dmesg** show about such USB flash or hard drive when you connect it?

---

### Post by aboud on 2010-12-05
the problem disappear after the latest kernel 2.35,  I didn't catch the dmesg before I update yesterday, hope it will be gone for good.

---

