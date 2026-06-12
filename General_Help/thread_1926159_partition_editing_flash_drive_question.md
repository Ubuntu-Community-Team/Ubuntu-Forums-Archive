---
title: "partition editing flash drive question"
date: 2012-02-15
forum: General Help
---

### Post by imachavel on 2012-02-15
hello I used this command:


sudo fdisk -l
[sudo] password for danel: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ded99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95379456   658579455   281600000   83  Linux
/dev/sda2       658581502   976771071   159094785    5  Extended
/dev/sda5       853129216   924809215    35840000   82  Linux swap / Solaris
/dev/sda6       658581504   776222719    58820608   83  Linux
/dev/sda7       776224768   781449215     2612224   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001342b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    31266815    15633392   83  Linux


it is /dev/sdc since it read 16.0 gb, I want to delete the partition, as I was going to format it with Linux mint OS, and had a bit of trouble surfing around the net finding a way to mount it, the file system on it, then to format the drive with the compressed .iso, which I believe would un compress it and write it as an uncompressed image. Anyway now I want to use the drive for file backups/transfers etc. since I'm getting lazy about transferring files through the network

I was trying to use this:

[http://www.cyberciti.biz/faq/linux-viewing-drive-partitions-with-fdisk-parted/](http://www.cyberciti.biz/faq/linux-viewing-drive-partitions-with-fdisk-parted/)

but it doesn't give too much information on how to delete a partition. I was thinking of booting to my gparted disk and realized the partition wouldn't be shown, at least to my best knowledge, because of the fact that it's not listed from the gparted application, attached is a screen shot, it only reads partitions on one disk? What if raid is installed? It'll read all partitions formatted and installed to internal hdd controllers?

You know, let's skip the raid question, I don't have raid installed. If anyone can help me figure out how to delete the partition on the San Cruz disk, I'd appreciate it

---

### Post by jerrrys on 2012-02-16
You cannot change drives in the upper corner?

[ATTACH]212781[/ATTACH]

Delete a partition

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

Have backup?  A good idea when working with gparted.

---

