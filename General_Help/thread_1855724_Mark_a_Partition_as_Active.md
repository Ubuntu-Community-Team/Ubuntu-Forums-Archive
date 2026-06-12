---
title: "Mark a Partition as Active?"
date: 2011-10-06
forum: General Help
---

### Post by Harry_G on 2011-10-06
I've got Ubuntu 10.4, and I have two hard drives connected to my PC. One is the drive that I boot from, and the other one is drive :Z.

I'm going to boot from drive :Z from now on. How do I mark it as active, so that my computer will recognize it on startup?

Also, I just started using Ubuntu this week, so if you could slow things down a little for me, that'd be great!

---

### Post by oldfred on 2011-10-06
Welcome to the forums.

Windows uses active or what in Linux we see as a boot flag. Grub or  grub2 do not use boot flag but find the partition with the code installed. Boot flag is in the partiton table in the MBR or first sector of hard drive.

BIOS controls which drive to boot from and jumps to the MBR of that drive. Newer BIOS that support SATA drives let you choose both boot device and which hard drive if boot device is a hard drive. Older PATA/IDE systems used jumpers on hard drives (SATA has no jumpers) or the location on the cable select cable for Primary Master and if in BIOS you select Hard Drive as boot device, BIOS will boot primary master.

What drive is z:?  In Linux we use sda, sdb etc as drives and sda1, sda2 as partitions. Windows mixes drives and partitions and calls all of them as drives. Often in Windows z: was a network device?

---

### Post by Harry_G on 2011-10-06
Thanks for replying so quickly!

By drive Z:, I meant that I named the drive Z: after I formatted it, just for the heck of it.

So you're saying that I can make this drive active, or boot flag it, by selecting it through BIOS?

---

### Post by bodhi.zazen on 2011-10-06
"drive Z:" makes no sense to your bios or linux.

See : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

If you want assistance on a Linux forums, please use the proper terminology, otherwise you are asking for mistakes / errors as we can not be sure what drive you are referring to.

You can set the partition as bootable with fdisk

sudo fdisk /dev/sdxy 

use the "a" option

[http://www.thegeekstuff.com/2010/09/linux-fdisk/](http://www.thegeekstuff.com/2010/09/linux-fdisk/)

or parted

sudo parted /dev/sdx set 1 boot on

see man parted

or gparted.

Although Linux does not use the boot flag, it is used by most (if not all) bios and at least one partition must be marked as bootable.

---

