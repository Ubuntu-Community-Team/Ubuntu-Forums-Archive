---
title: "RAID - fdisk funny info..."
date: 2009-12-27
forum: General Help
---

### Post by duffed on 2009-12-27
Hi,
 
I have setup 2 HD of 1TB as Software RAID1. 
 
Into the mdadm.conf I have:
 
DEVICE /dev/sdb1 /dev/sdc1
ARRAY /dev/md0 level=raid1 devices=/dev/sdb1,/dev/sdc1
 
The RAID auto start on boot and that perfect.
 
But the RAID look weird in fdisk and Palimpset
 
with I do fdisk -l I see:
 
Disk /dev/md0: 1000.2 GB, 1000202101760 bytes
2 heads, 4 sectors/track, 244189966 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x2052474d
 
This doesn't look like a partition table
Probably you selected the wrong device.
 
Device Boot Start End Blocks Id System
/dev/md0p1 ? 822447 240553456 958924038+ 70 DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/md0p2 ? 244156454 471478443 909287957+ 43 Unknown
Partition 2 does not end on cylinder boundary.
/dev/md0p3 ? 28216909 28216910 5 72 Unknown
Partition 3 does not end on cylinder boundary.
/dev/md0p4 330301441 330307927 25945 0 Empty
Partition 4 does not end on cylinder boundary.
 
And Palimpset.. see attach.
 
this is into my fstab
 
# Entry for /dev/sda1 :
UUID=f0e0afee-6679-4fde-9d72-1928e47ea0c5 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=726fd2de-c36a-485a-8877-b42984f98b32 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/md0 /media/Multimedia ntfs-3g defaults,locale=en_US.UTF-8 0 0
 
The funny part is I can see the Drive Mount and when I open it it toll me I have 932GB free, that normal as they RAID is still empty.. but I find weird what I see in fdisk..
 
Thanks for your help.
 
Seb

---

### Post by skulls on 2010-08-26
Hi,

I am really surprised. I have the exact same problem as you. And when I say exact, I mean it; the output of both fdisk and palimpsest is *exactly* the same, with the same strange partitions md0p1, md0p2.. and their respective start and end boundaries!!
It's like you have the exact same setup!

I came across this post because I just recently converted my RAID1 array from ext4 to ntfs and the end result is working, but these strange reports from fdisk and palimpsest make me wonder whether there's something wrong and I might lose all the information :(

Did u finally find out what was wrong? Can somebody please enlighten?

Thanks!

---

### Post by srs5694 on 2010-08-26
See my reply in [this thread.](http://ubuntuforums.org/showthread.php?t=1561508)

---

