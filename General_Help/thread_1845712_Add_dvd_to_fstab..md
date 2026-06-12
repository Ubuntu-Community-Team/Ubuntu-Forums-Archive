---
title: "Add dvd to fstab."
date: 2011-09-17
forum: General Help
---

### Post by ranjithnair on 2011-09-17
I had edited /etc/fstab to automount partitions early. Yesterday I bought a sata dvd-writer and my hdd is IDE. Now I am not able to access my dvd because of /etc/fstab setting. Can somebody tell the solution.(How to add back the dvd to fstab or any other suggestion)

sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7adf7ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          19      151552   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          20        3038    24250117+   7  HPFS/NTFS
/dev/sda3            3039        8260    41945684+   f  W95 Ext'd (LBA)
/dev/sda4            8261        9729    11799742+   c  W95 FAT32 (LBA)
/dev/sda5            3039        5649    20972826    b  W95 FAT32
/dev/sda6            6731        8260    12289693+   7  HPFS/NTFS
/dev/sda7            5650        6730     8681472   83  Linux


```

/etc/fstab contents
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=ddd34597-3d14-4c8a-a160-8b801e552ea5 /               ext4    errors=remount-ro 0       1
UUID=a7646169-4bc1-4ffe-a96f-93d143f352b5 none            swap    sw              0       0

/dev/sda2 /media/WINDOWSXP ntfs-3g auto defaults 0 0
/dev/sda5 /media/SOFTWARE vfat user,fmask=0111,dmask=0000 0 0
/dev/sda4 /media/MOVIES vfat user,fmask=0111,dmask=0000 0 0
/dev/sda6 /media/SONGS ntfs-3g auto defaults 0 0
```

---

### Post by DukeBoxer on 2011-09-17
That might be something you need to configure in the BIOS instead. Not sure though. I'm not sure the DVD would show up in the fstab file since it is for file systems. Here is my fstab file and there is no DVD player even though I have one hooked up, also a multi-card reader, and again no mention of it. fstab is for what gets mounted on startup, not what you have hooked up.

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=---- /               ext4   discard,errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=---- /home           ext4    discard,defaults        0       2
# /tmp was on /dev/sdb2 during installation
UUID=---- /tmp            ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=---- /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=---- none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
#UUID=---- none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
/dev/sdb5	/media/Storage	ext4	defaults	0	2

---

### Post by ranjithnair on 2011-09-18
Even I think so...do we have to reconfigure ubuntu after installing an sata dvd drive....?

---

### Post by gandaran on 2011-09-18
> Yesterday I bought a sata dvd-writer and my hdd is IDE
does BIOS support SATA hardware? can you see the dvd drive detected in BIOS?

---

### Post by ranjithnair on 2011-09-18
Yes..Bios detects the sata hardware...
I think its some problem with grub...can anyone tell if the grub needs to be configured after installing sata hardware...?

---

### Post by searchfgold6789 on 2011-09-18
No, no no. Grub has nothing to do with this sort of thing.
Anyway, your DVD drive is simply a piece of hardware, nothing else. However, when you insert a disk into it, it becomes a spinning, deathly, silver instrument of highly advanced data input and output, rather like your hard disk. You may be able to auto-mount a DVD, but you are not able to auto-mount a DVD drive. I personally do not know how to auto-mount a DVD.
I would double-check to see if your drive officially works with linux.
Good luck,
 - search

---

### Post by ranjithnair on 2011-09-18
It will work with ubuntu...sometimes it gives grub error and sometimes after retrying it boots with dvd drive working...dono wats the problem..

---

### Post by MrSpike16 on 2011-09-18
Mixing PATA (IDE) and SATA can be a nightmare especially on computers that are a few years old.  My solution is to convert one drive so both use the same interface either PATA or SATA.

Here is a link to give you an idea to what I am talking about: [http://www.avlab.com.tw/sata/1006_0104_000bx.htm](http://www.avlab.com.tw/sata/1006_0104_000bx.htm)  

You can get them to go from PATA hard drive to SATA or SATA hard drive to PATA and I have both of these handy adapters.

These shouldn't cost more than a few dollars.  Some retailers charge way too much.

Sometimes this is the only solution to get both drives seen by BIOS and OS.

There are no drivers required either.

---

### Post by ranjithnair on 2011-09-18
I think you are right...My computer boots sometimes and sometimes it doesnt and i have to keep restarting till it does boot...

---

### Post by MrSpike16 on 2011-09-18
If you are buying the SATA hard drive to PATA (IDE) adapter make sure it has a switch or jumper so it can be used for Slave or Master.

Been awhile since I bought, but at that time there were ones that only worked as Master.

---

### Post by ranjithnair on 2011-09-19
Thanks spike...it was very helpful...I am planning to buy new harddisk..

---

### Post by ranjithnair on 2011-10-27
Reinstalled Ubuntu everything is fine....Some grub issue..

---

