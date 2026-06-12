---
title: "Permissions for a new HDD..."
date: 2006-06-20
forum: General Help
---

### Post by mootchell on 2006-06-20
Hi. I recently bought a new HDD, 200 GB, nothing too special. However, I dual boot Windows with Ubuntu 6.06 and I installed the HD while still using Windows (So it's NTFS, not ext2). Now, I am trying to gain permission to write to it from my user name in Ubuntu, but I can't get it to recognise.. I keep getting an error saying that /media/hdb1 is a red-only file system.

I tried chmod 777 to no avail. Someone, please let me know if it's even possible to write to this drive from Ubuntu! And if not, if I can somehow convert the file system from NTFS to ext2?

---

### Post by ifokkema on 2006-06-20
[QUOTE=mootchell]Hi. I recently bought a new HDD, 200 GB, nothing too special. However, I dual boot Windows with Ubuntu 6.06 and I installed the HD while still using Windows (So it's NTFS, not ext2). Now, I am trying to gain permission to write to it from my user name in Ubuntu, but I can't get it to recognise.. I keep getting an error saying that /media/hdb1 is a red-only file system.

I tried chmod 777 to no avail. Someone, please let me know if it's even possible to write to this drive from Ubuntu! And if not, if I can somehow convert the file system from NTFS to ext2?[/QUOTE]

NTFS is read-only by default. It's a Microsoft filesystem and they don't provide open source drivers to work with it.

You can use gparted to graphically reformat the partition with a different filesystem type. If you like the console, you can use fdisk.

---

### Post by bruce89 on 2006-06-20
FAT32 would work for writing from Windows and Linux.

---

### Post by AdamTheCamper on 2006-06-20
I solved this problem with ' gsudo Krusader '. I still can't write to my ntfs with linux, but at least I can easily access files,and work with them by copying on my ext3 partition. When I need them back on windows I use Total Commander ext3 plug in.
I dont know if there is some better way...

---

### Post by bruce89 on 2006-06-20
As I said before, if you want the partition to be writable from both Windows and Ubuntu, use FAT32.  The problem with FAT32 is the maximum size of files being 4GB I think.

---

### Post by ifokkema on 2006-06-20
[QUOTE=bruce89]As I said before, if you want the partition to be writable from both Windows and Ubuntu, use FAT32.  The problem with FAT32 is the maximum size of files being 4GB I think.[/QUOTE]
As far as I can deduce form the original post, it was not requested to provide a solution for both windows and linux writing to the partition, but just Linux... If he doesn't need windows to write to that partition, I would recommend ext3. Else, FAT32 sounds good.

The max of 4 GB a file on FAT32 is correct. Also, Windows can't format FAT32 partitions bigger than 32 GB.

---

