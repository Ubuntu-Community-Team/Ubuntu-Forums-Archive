---
title: "ubuntu dual boot reformat"
date: 2012-01-29
forum: General Help
---

### Post by navidson on 2012-01-29
hey there I'm somewhat new to all this and not that savvy but i have a dual boot with ubuntu and xp and want to just have ubuntu can someone direct me to the right walk through that will help me get this done. i have an inspiron 1525 and want to reformat and have only ubuntu 10.04 thanks.

---

### Post by drs305 on 2012-01-29
Without seeing your specific layout here is what I suspect you have (others may ask, so you could post the results of "sudo fdisk -l").

```

Primary partition - sda1 Windows
Extended partition - sdaX
  Logical partition - sda5 Ubuntu
  Logical partition - sda6 swap

```

The numbers don't really matter in the example, provided Ubuntu has been installed on a logical partition.

What I'd recommend is
1. Shrink the Windows partition, but keep at least one primary partition.
2. Reformat it to whatever format you want (the Ubuntu default is now ext4).
3. Expand the extended partition 'to the left'.
4. Either:
a) expand or move Ubuntu to fill the newly created space. This will take a bit of time, and moving/expanding partitions 'to the left' always involves a slight chance of data loss
or 
b) create a data partition with the new space on the left.

I'd recommend doing all of this from a LiveCD, since you can't work with mounted partitions. Even from the LiveCD, you will need to unmount the swap partition.

I have some instructions in the following guide for shrinking Windows and expanding /, which is what I recommend above. There is also a link at the bottom of the first post for a guide by *srs5694* that is very good.

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by Rodney9 on 2012-01-29
This site will help will a easy guide -

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Basically you just need to **back-up** any data (docs, photos,music etc) then boot from the Ubuntu cd/dvd for a full install again and this time tell it to use *all* the hard drive.

Other very good tips after the install, thanks to TrakerJon -

[http://ubuntuforums.org/showthread.php?t=1469825](http://ubuntuforums.org/showthread.php?t=1469825)

Rodney

---

### Post by navidson on 2012-01-29
so here are the results.
my friend just used gparted to delete the partition so now it's sitting there unallocated. i don't have the live cd so i have a usb using unetbootin but it won't load even after changing the bios to usb. it just said nothing was detected...i think i may be out of my league haha.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe5bfe5bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           12494       38914   212219905    5  Extended
/dev/sda5           12494       37837   203574272   83  Linux
/dev/sda6           37838       38914     8644608   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders
Units = cylinders of 2816 * 512 = 1441792 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2782     3915772    c  W95 FAT32 (LBA)

---

### Post by navidson on 2012-01-29
thank you very much mission accomplished guys.

---

