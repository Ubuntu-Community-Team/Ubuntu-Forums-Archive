---
title: "Creating a Shared FAT32 partition"
date: 2010-10-03
forum: General Help
---

### Post by Metallover on 2010-10-03
I am dual booting windows 7 and ubuntu 10.04 using grub.  I am using a 1tb samsung hard drive.  Ubuntu has 750gb and windows has 250gb.  I want 500gb of my HD to be FAT32 so I can put all of my music, pictures, and videos on it.  I don't have more than 100gb used on either partition.

I have done quite a bit of searching and browsing, but I can't find a good step by step guide to do this.  I am guessing I need to figure out how to use fdisk?

---

### Post by btindie on 2010-10-03
So you just want to resize your partitions to create space for a 500GB data partition?
 
First off defrag the windows partiton so it can be resized. Then use [Parted Magic]("http://partedmagic.com/") to resize your partitions and create the new one. You can burn it to CD or boot it from a USB stick, see UNetbootin for that.
 
Do you just have the two partitons or are there others? Can you post the output of ```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2010-10-03
> **Metallover said:**
> I want 500gb of my HD to be FAT32 so I can put all of my music, pictures, and videos on it...

No you don't -- believe me.  You need it to be NTFS.  FAT32 limits file sizes and is not nearly as robust as NTFS.

---

### Post by Metallover on 2010-10-03
When I enter sudo fdisk -l I get this

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bfa6bfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       91201   732467456    7  HPFS/NTFS
/dev/sda3           91201      121602   244190209    5  Extended
/dev/sda5           91201      120365   234253312   83  Linux
/dev/sda6          120365      121602     9935872   82  Linux swap / Solaris

I said I wanted fat32 because I heard ntfs was buggy,, However that has probably changed.  ntfs it is.

I'll give parted magic a try.

Thanks for all your help!!

---

