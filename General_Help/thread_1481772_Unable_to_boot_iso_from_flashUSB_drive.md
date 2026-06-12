---
title: "Unable to boot iso from flash/USB drive"
date: 2010-05-12
forum: General Help
---

### Post by dhaze579 on 2010-05-12
Hello all...

I am trying to make an iso boot from a 8GB SanDisk Cruzer USB drive through UNetBootin, and it's just not happening. I have tried several times, but always had the same disappointing result. It looks like when UNetBootin goes through the process of putting it on the flash drive, it completely skips aking it bootable. Any suggestions? Maybe it is just UNetBootin.

Thanks.

BTW, I'm running Ubuntu.

---

### Post by efflandt on 2010-05-12
I have never used unetbootin, just the Startup Disk Creator in Ubuntu.  What happens when you try to boot it and which Ubuntu version iso is it?  Note that a file cannot be larger than 4 GB - 1 byte on FAT32, so if you have a persistent file, it should be less than 4 GB.

If you do an actual installation on USB, you have to make sure that you put grub on the USB drive (instead of default to your main hard drive) from the Advanced button in step 8.  But a bootable iso does not use grub.

By default 10.04 uses a kernel mode (KMS) driver for certain video cards that can trip some people up (some end up with no video at all).  The only problem I had with that was that it slowed up my system and broke suspend/hibernate.  If you can get the first screen with graphics at the bottom, hit any key and try adding **nomodeset** kernel parameter to use user space video (and possibly remove **splash** parameter).

PS: If that Cruzer has U3, that can greatly extend boot time, because it contains a pseudo cdrom device in it too.

---

### Post by ryan858 on 2010-05-12
Yeah, try it with Startup Disk Creator and see if it works... If it's still not marked bootable, then you can use **cfdisk** to add a bootable flag. The command would be something like:

$ cfdisk /dev/sdb

Replace 'sdb' with whatever your usb drive is... Make sure not to use 'sdb1' or 'sdb2' or anything... Put the whole disk, otherwise you'll get errors saying the partitions are messed up (because you tried to open a partition as a disk)

You can check which dev your usb is on by typing **fdisk -l**.

And if U3 is installed on the stick, you might want to remove it if you're going to use it as a boot disk. You can always download it and install it back on if you need to, I think it's available on the Sandisk website, I could be wrong though...

---

