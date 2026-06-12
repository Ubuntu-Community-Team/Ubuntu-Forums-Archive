---
title: "copy HDD to new that has been set up with lvm"
date: 2010-10-05
forum: General Help
---

### Post by jquis8411 on 2010-10-05
I was hoping to copy my existing hdd to a new one that has lvm and for whatever reason(inexperience) I cant figure out a good way to do it. This is what Im working with old drive =160GB, new drive 500GB.
new drive fdisk
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f891

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1          26      204800   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3              26        1070     8388608   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sdb4            1070       60802   479792152   8e  Linux LVM
Partition 4 does not end on cylinder boundary.

sdb2 should be boot 200M, sdb3 is a swap 8GB and sdb4 is all lvm with a 15 gb logical volume  
 meh@meh-desktop:~$ sudo pvs
  PV         VG     Fmt  Attr PSize   PFree  
  /dev/sdb3         lvm2 --     8.00g   8.00g
  /dev/sdb4  lovog1 lvm2 a-   457.56g 442.56g
meh@meh-desktop:~$ sudo lvdisplay /dev/lovog1/base
  --- Logical volume ---
  LV Name                /dev/lovog1/base
  VG Name                lovog1
  LV UUID                zZyPTU-DN8G-dm2b-pWjL-ia90-aeM1-cbpgxe
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                15.00 GiB
  Current LE             3840
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
I hope that this info helps someone think of a plan because im lost at what I figured would be the easy part. TY

---

### Post by jerome1232 on 2010-10-05
Is the old drive using lvm too? You can add it into the same volume group as your new drive and pvmove the volumes off of it.

If the old drive is using standard partitions, I would simply create new partitions that are after your physical volume for lvm and copy the data over, I'm not familiar enough with dd and/or partition table editing to know exactly how to clone the partitions one by one over to new spots on your new drive.

---

### Post by jquis8411 on 2010-10-05
No the old drive is just a standard install. 150GB of wide openext4 and a little ext partition for 6gb swap.I was thinking to just copy  my home to the 15 gb lvm logical volume and roll with that but for the life of me I cant figure out a command to do accomplish this. I have no idea whats going on with dd and tar but id like to learn a couple of things in the process.

---

### Post by jquis8411 on 2010-10-05
I figured it out using rsync  #rsync -avx / then to my mounted logical volume. wash rinse repeat for swap and what not. TY

---

