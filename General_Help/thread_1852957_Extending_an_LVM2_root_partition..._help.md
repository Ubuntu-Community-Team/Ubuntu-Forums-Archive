---
title: "Extending an LVM2 root partition... help?"
date: 2011-10-01
forum: General Help
---

### Post by docksteaderluke on 2011-10-01
I have a single 300GB HDD with Ubuntu on it (LVM2 with 3 LVs, root, swap and home). I'm getting "Low disk space" notices for the root LV so I need to extend it.

The problem is... I can't seem to figure out how to do it without destroying everything.

What I'm aiming to do is reduce the size of the home LV and add that free space to the root LV because I don't have another hard drive that I can add to the VG.

Here's the output of my lvdisplay:

```
  --- Logical volume ---
  LV Name                /dev/VG/root
  VG Name                VG
  LV UUID                --------------------------------
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                6.52 GiB
  Current LE             1668
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/VG/swap
  VG Name                VG
  LV UUID                -----------------------
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.72 GiB
  Current LE             953
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1
   
  --- Logical volume ---
  LV Name                /dev/VG/home
  VG Name                VG
  LV UUID                ---------------------------
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                287.38 GiB
  Current LE             73570
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:2

```

Any help would be greatly appreciated!

---

### Post by docksteaderluke on 2011-10-06
After pulling my hair out for many days trying to figure this out (new to LVM) I found this tutorial (linked below). But in summary the steps I followed were the following:

1. Check both file systems with: e2fsck -r PARTITION
2. Reduce 1st partition's file system: resize2fs PARTITION SIZE
3. Reduce 1st partition's LV size: lvreduce -L SIZE PARTITION (use +/- for relative sizing)
4. Expand the file system to ensure it has the correct block size: resize2fs -p PARTITION
5. Extend the 2nd partition's LV size: lvextend -L SIZE PARTITION
6. Extend the 2nd partition's file system: resize2fs -p PARTITION (this will automatically extend it to the max size allowed by the LV)

[Tutorial]("http://askubuntu.com/questions/33593/how-can-i-either-free-up-enough-space-on-root-or-resize-my-partitions")

---

