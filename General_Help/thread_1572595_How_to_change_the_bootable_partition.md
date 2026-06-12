---
title: "How to change the bootable partition?"
date: 2010-09-11
forum: General Help
---

### Post by justshams on 2010-09-11
Hi, I installed ubuntu 10.04 on my HDD, and loved it, hence decided to keep it and trash the other OS(s).
But facing one problem.
Attached is the screen shot of my HDD mapping
The New Volume is where windows Xp used to be, and the 20GB Ext2 drive is where my ubuntu is.
Now as u can see, the New Volume Drive is a boot able, but i want to make the ubuntu drive bootable,
I tried this by removing the bootable flag form the new volume and assigning that to the ubuntu partition, but that resulted int eh system giving the error "no mood media found - insert boot disk and then press any key"
I then had to use a live CD to restore the flags and then was able to boot.
Kindly Guide me through the process. Thanks
Here is also the o/p of fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3917    31463271    7  HPFS/NTFS
/dev/sda2   *        3918        6528    20972857+   7  HPFS/NTFS
/dev/sda3            6529       19458   103853857+   f  W95 Ext'd (LBA)
/dev/sda5            6529       10080    28523517+   7  HPFS/NTFS
/dev/sda6           10080       12569    19998720   83  Linux
/dev/sda7           12569       12694      999424   82  Linux swap / Solaris
/dev/sda8           12694       19458    54329344    b  W95 FAT32

---

### Post by dcstar on 2010-09-11
> **justshams said:**
> Hi, I installed ubuntu 10.04 on my HDD, and loved it, hence decided to keep it and trash the other OS(s).
But facing one problem.
Attached is the screen shot of my HDD mapping
The New Volume is where windows Xp used to be, and the 20GB Ext2 drive is where my ubuntu is.
Now as u can see, the New Volume Drive is a boot able, but i want to make the ubuntu drive bootable,
........

Do a web search on reinstalling Grub2, you should find detailed instructions on installing the boot loader where you want it.

---

### Post by 73ckn797 on 2010-09-11
For a specific Ubuntu search use this search link: [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

Look here also: [http://ubuntuforums.org/showthread.php?t=1037538](http://ubuntuforums.org/showthread.php?t=1037538)

---

