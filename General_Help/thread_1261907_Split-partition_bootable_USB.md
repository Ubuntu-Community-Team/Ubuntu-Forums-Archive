---
title: "Split-partition bootable USB?"
date: 2009-09-09
forum: General Help
---

### Post by ChewyNougat on 2009-09-09
Hi all,

I am trying to accomplish the following: I have an 8 GB USB jumpdrive on which I want two partitions, a 1 GB bootable Ubuntu partition, and a 7 GB data partition. I have attempted to partition the drive and format it several different ways, but I always get a "Boot Error" message (that's all it says) when trying to boot from the partitioned USB drive. If I dedicate the whole drive to being the boot partition, it works. 

Any of you guys (or girls, as it were) know whether or not this is possible?

Thanks!

---

### Post by C.S.Cameron on 2009-09-09
You should be able to take the working flash drive with the single partition and add a second FAT32 partition on the left hand side using gparted. Windows will only see the first partition on a flash drive.
If you want the drive to be persistent you should probably leave more than 1G.
I seem to recall that this method might screw up grub and grub may need to be reinstalled.
Another method that I know works is to start with two partitions, the first being smaller than 700MB. This will force usb-creator to install to the second partition. The partitions can then be re-sized using gparted.

---

### Post by squashpup on 2010-01-01
I used Gparted to partition my 32gb SanDisk Cruzer into a 26GB, and a 6GB. 

Used the USB Startup Disk Creator to put 9.10 on the second partition.  I chose the second because I wanted a storage partition and Windows never seems to be able to find the second partition on a USB drive for some reason.  So, if I use the FIRST partition as storage, it should be accessible from both Windows and from my live USB UBUNTU boot.

Works great, except now, I tried to make a startup CD so I could use my Ubuntu USB on computers that don't boot from USB.  And, you guessed it, the boot CD can't find the bootable Ubuntu partition on the USB.  So, I'm off to figure out how to get this thing to boot.

---

