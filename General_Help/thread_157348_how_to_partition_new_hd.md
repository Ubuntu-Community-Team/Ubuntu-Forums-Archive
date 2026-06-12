---
title: "how to partition new hd?"
date: 2006-04-08
forum: General Help
---

### Post by orlox on 2006-04-08
Well, I'm pretending to buy a 300g sata hard drive, and I need to decide on how to make the partitions on it. I think I'll use dual booting with a windows partition (wich I barely use, but sometimes truly need), an ubuntu partition, and a shared partition for both of them. 
My current HD is partitioned this way, being the shared partition a FAT32. But as far as I know, FAT32 has a file size limit (4 gigs I think). Does anyone know of another way of getting this to work like this, without that file size limit? Or any other way to allow linux and windows to efficiently share files of any size?

---

### Post by nanotube on 2006-04-08
[QUOTE=orlox]Well, I'm pretending to buy a 300g sata hard drive, and I need to decide on how to make the partitions on it. I think I'll use dual booting with a windows partition (wich I barely use, but sometimes truly need), an ubuntu partition, and a shared partition for both of them. 
My current HD is partitioned this way, being the shared partition a FAT32. But as far as I know, FAT32 has a file size limit (4 gigs I think). Does anyone know of another way of getting this to work like this, without that file size limit? Or any other way to allow linux and windows to efficiently share files of any size?[/QUOTE]

fat32 is really the most "tried and true" way to do it. there is some driver for win that can read/write ext2, and there is some driver for ubuntu that can read/write ntfs... but unless you really plan on shoving >4gig files around between the twy os all the time, just go with fat32 and save yourself some trouble. :)

---

### Post by orlox on 2006-04-09
I pretend to use the shared partition to hold all of my documents and files that are not dependant of the different OS's my pc has. So having the possibility of getting files bigger than 4 gigs would be pretty convenient, to keep things like dvd images...But if the only thing thats completely trustworthy is FAT32, I guess I'l just use that.

now that I remember, I have another question...I have utf-8 as the charset for the FAT32 partition, but when mounting it, ubuntu says something about "utf-8 not being a reccomended charset" because it would make the filesystem case-sensitive...what charset am I supossed to use then?

---

