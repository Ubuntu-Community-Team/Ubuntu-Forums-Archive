---
title: "Mounting drives permanently?"
date: 2011-08-23
forum: General Help
---

### Post by F1lthym0nk3y on 2011-08-23
I have tried using storage device manger but cannot find an option to make all drives mounted all the time? How can I have all my drives mounted upon booting?

---

### Post by Megaptera on 2011-08-23
Hi,
Have you tried this guide? [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by seawolf167 on 2011-08-23
You'll want to add entries to /etc/fstab to have them mounted at boot time.

If you post the output to the following commands we can help you format the entries, else you can take a look at [this link ]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")for more information (same one as previously posted by Megaptera)

```
sudo fdisk -l
sudo blkid
mount
```

---

### Post by F1lthym0nk3y on 2011-08-23
```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb96e290

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      176027  1413935100    7  HPFS/NTFS
/dev/sda2   *      176027      182402    51200000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88a28261

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976758784    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10254d6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         244     1951745    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sdc2             244        9970    78125056   83  Linux
/dev/sdc3            9970       60802   408306688    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdc5               1         244     1951744   82  Linux swap / Solaris

Disk /dev/sdd: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00067b8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       48642   390709248    7  HPFS/NTFS

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc715391e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953509463+   7  HPFS/NTFS

```

```
/dev/sda1: LABEL="Downloads" UUID="DA9C94729C944AC1" TYPE="ntfs" 
/dev/sda2: LABEL="Windows7" UUID="3A0897110896CB71" TYPE="ntfs" 
/dev/sdc2: UUID="fa9b424b-c1c6-4d1b-8f15-09005e7d2155" TYPE="ext4" 
/dev/sdc3: LABEL="Ubuntu + Downloads" UUID="3E60DAD160DA8ED1" TYPE="ntfs" 
/dev/sdc5: UUID="dcb5c1eb-7317-4f2f-9368-991eb3f61cd4" TYPE="swap" 
/dev/sdd1: LABEL="New Downloads" UUID="781EA2521EA208E8" TYPE="ntfs" 
/dev/sde1: LABEL="Brads Movie Collection Part 2" UUID="0220DBDA20DBD2B1" TYPE="ntfs" 
/dev/sdb1: LABEL="Music>Work>Files" UUID="BCEE1DEBEE1D9EA8" TYPE="ntfs" 

```

```
/dev/sda1: LABEL="Downloads" UUID="DA9C94729C944AC1" TYPE="ntfs" 
/dev/sda2: LABEL="Windows7" UUID="3A0897110896CB71" TYPE="ntfs" 
/dev/sdc2: UUID="fa9b424b-c1c6-4d1b-8f15-09005e7d2155" TYPE="ext4" 
/dev/sdc3: LABEL="Ubuntu + Downloads" UUID="3E60DAD160DA8ED1" TYPE="ntfs" 
/dev/sdc5: UUID="dcb5c1eb-7317-4f2f-9368-991eb3f61cd4" TYPE="swap" 
/dev/sdd1: LABEL="New Downloads" UUID="781EA2521EA208E8" TYPE="ntfs" 
/dev/sde1: LABEL="Brads Movie Collection Part 2" UUID="0220DBDA20DBD2B1" TYPE="ntfs" 
/dev/sdb1: LABEL="Music>Work>Files" UUID="BCEE1DEBEE1D9EA8" TYPE="ntfs" 

```

---

### Post by seawolf167 on 2011-08-23
Looks like you have 5 partitions (4 NTFS volumes) you want mounted at boot? (sda1, sda2, sdc, sdd, sde)

If so, I think the easiest thing to do (since they are all NTFS formatted) would be to use *ntfs-config* to add those entries to /etc/fstab.

```
sudo apt-get install ntfs-config
```

You can then launch it from a terminal by typing

```
gksudo ntfs-config
```

And it'll do all the configurations for you

---

### Post by BHEJU on 2011-08-23
Hi
I had the same question few weeks back.
I found the same page (mentioned in previous post).

And gave shot to pysdm:
sudo apt-get install pysdm

Here is the thing. You should understand how fstab works.
But even though I am comfortable with bash/terminals. I feel more comfortable with GUI.
And pysdm is very easy to use.

Cheers,

---

### Post by seawolf167 on 2011-08-23
Psydm works, however, I don't think it is being maintained anymore.

---

### Post by Morbius1 on 2011-08-23
And ntfs-config hasn't been maintained since the Carter administration. Plus it doesn't seem to know that ntfs partitions are already write enabled by default which is kind of spooky.

Anywho, based on his post:
> I have tried using storage device manger but cannot find an option to make all drives mounted all the time? Isn't that Pysdm?

Rather than using one GUI to fix another it might be interesting to see what damage has already been done:
```
cat /etc/fstab
```

---

