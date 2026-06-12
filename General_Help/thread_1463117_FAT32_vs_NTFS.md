---
title: "FAT32 vs NTFS"
date: 2010-04-26
forum: General Help
---

### Post by Azyx on 2010-04-26
Hi.
I purchased a FREECOM 1,5TB external USB-HDD and find out that there was FAT32 as FS. I windos there are not posasible to make bigger FAT32-partition than 32GB. 
I wan't to have windos-FS to use my work and on my freinds computers.
Do you think I could format to NTFS or keep the FAT32? I don't have any big files.
/Cheers

---

### Post by kvarley on 2010-04-26
You can easily format harddrives and other flash media etc using gparted.

> sudo apt-get install gparted

Then hit Alt+F2 and type:
> 
gksudo gparted

Input your password, select your hard drive when gparted loads - right click on it & format to ntfs.

---

### Post by jetsam on 2010-04-26
I'd do one or two 80 Gig NTFS partitions and use the rest for ext3 or ext4.  It depends on how much you plan to do with it, though.  If you have to pick just one, I guess I'd say use ntfs.  It's too big a drive to mess around with fat32 as a primary partition, but you could stick a fat32 partition on there if you have special file sharing needs.  

Fat32 is nice because almost everything can read and write to it, but it's too limiting for an os partition or a major hard drive.

---

