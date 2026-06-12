---
title: "hfsplus : partition size not a multiple of 4K"
date: 2009-12-12
forum: General Help
---

### Post by Kimos on 2009-12-12
I have a new 1TB USB hard drive. I dropped the NTFS partition it came with and want to format it HFS+ to use on both my Ubuntu machine and my Mac machine.

I've tried from the command line and from gparted, on multiple sizes of partitions, and invariably get this result:

```

$ sudo mkfs.hfsplus -v "BACKUP" /dev/sdd1 
mkfs.hfsplus: /dev/sdd1: partition size not a multiple of 4K.

```

fdisk gives:

```

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8c1dfde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121600   976751968+  83 

```

I also tried with 1-121601 with the same.

Ideas? Seems to be saying that my partition needs to be a certain size, but gparted was sizing in even MB which would be a multiple of 4KB.

I can't even find reference to this error anywhere except on Mac forums for Disc Utility...

---

### Post by Leppie on 2009-12-12
have you tried using gparted to convert to hfs+?

---

### Post by Kimos on 2009-12-12
You mean to first format it as ext3 or something then convert it to hfs+? No, I did not.

I'm testing it right now but I ended up plugging the drive into my Mac and formatting it from there. I got the same 4k error in Disc Utility the first time, but I switched from Master Boot Record to GUID Partition Table and that took.

Plugged it back into my Ubuntu machine and it took some playing with the mounts but got it to recognize. Copying over data now and will bring it back to the Mac in a few to make sure it all stays stable.

Still doesn't explain the problem though.

---

### Post by srf21c on 2009-12-27
I'm getting the same "partition size not a multiple of 4K" trying to format a 1TB samsung drive using gparted 0.4.5 on Ubuntu Karmic.

Did some experimentation and if I create an HFS+ partition ~800GB or under, it will format using gparted.  Anything bigger and it throws the 4k error whilst formatting.

Drive resides in a Newertech v3 ministack enclosure and is connected via eSata.

---

### Post by Kimos on 2009-12-28
My drive bricked so I'm going to have to do it all over again. Still no resolution without plugging it into my Mac.

---

### Post by srf21c on 2009-12-28
It may be worth noting that according to S.M.A.R.T, my particular hard drive not in perfect health either.  I have already experienced some data loss on the 2nd HFS+ partition of the disk, along with S.M.A.R.T. error "threshold exceeded on attribute 184". 

I have since wiped the disk using Samsung's ESTOOL "low level format" (actually I'm pretty sure this is simply a drive re-initialization).

So whether or not the disk errors are at fault, or this is some large drive hard drive translation issue remains to be seen until I can get a replacement hard drive of equivalent size.

---

### Post by AleXoundOS on 2010-05-01
in the file newfs_hfs.c in sources i found:
```

/*
         * Above 512GB, enforce partition size to be a multiple of 4K.
         *
         * Strictly speaking, the threshold could be as high as 1TB volume size, but
         * this keeps us well away from any potential edge cases.  Besides, partitions
         * this large should be 4K aligned for performance.
         */
        if ((dip.totalSectors >= 0x40000000) && (dip.totalSectors & 7))
            fatal("%s: partition size not a multiple of 4K.", device);
```After some experiments I managed to create 651GB HFS+ partition with 1367179632 sectors in it on MBR partition table. This number divides without remainder by 2,3,4,6,7,8 and 9. Everything except 5. I have not tested yet, but I think that if you want to create a partition bigger than 512GB, then you need the number of sectors with that divisors. May be something which is a multiple of 2*3*4*6*7*8*9=72576.

---

