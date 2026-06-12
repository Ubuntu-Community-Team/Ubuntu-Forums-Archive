---
title: "Help restore partition table with fdisk (after parted/testdisk mess)"
date: 2011-01-28
forum: General Help
---

### Post by nick55 on 2011-01-28
Please help me restore my partition table.

what I did was:
- have NTFS (450GB + 4GB linux-swap + 44GB ext3 with ubuntu 10.10 upgraded from ubuntu 10.4). Ntfs partition contains data only, no windows.

- either with partition magic or paragon I tried to resize the NTFS and since then parted doesn't like my partitions anymore, but Ubuntu boots and works just fine..

- I took the output from fdisk -l and decided to remove the swap partition - ubuntu won't boot saying it needs the swap (although it was never mounted and i deleted the swap while ubuntu was active)



 I have the following output from fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78f2abc5

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       53856   432590728+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           53856       54390     4297387+  82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3           54391       60801    51490952+  8e  Linux LVM



and I have the expert data too:
Expert command (m for help): p

Disk /dev/sda: 255 heads, 63 sectors, 60801 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 239  63 1023         63  865181457 07
 2 00 239  63 1023 239  63 1023  865180575    8594775 82
 3 00 254  63 1023 254  63 1023  873786160  102981905 8e
 4 00   0   0    0   0   0    0          0          0 00

- then I tried TestDisk, it discovered some older partition table (before partition magic or paragon)
=> Ubuntu wouldn't boot - GRUB recovery> prompt showed.

- then I started editing the partition table with parted - removed everything and added it back together based on fdisk -l output => problem is that the second output looks different..

- now TestDisk won't recover much


**NOTE: Since the partitions are not on cylinder boundaries, using parted to recreate the partition table may not be good enough.. Please help! I'm way over my head here.. And unfortunately, I don't have a backup of the partition table.

---

### Post by psusi on 2011-01-28
Partition Tragic screwed up your resize and made the windows partition overlap your swap partition.  Delete the swap and Ubuntu will boot just fine without it.  Better yet, delete the swap partition, then use gparted to recreate it so that it will not overlap with the ntfs partition.

---

### Post by nick55 on 2011-01-28
As mentioned above, I did delete the swap, but Ubuntu didn't want to start - it wanted to mount the swap partition and would hang if I just press "ENTER" to continue.

Then I used TestDisk, but it brought back some older version of the partitions and GRUB wouldn't boot anymore..
Then I messed up everything with parted - deleted all partitions and added them again.. now i have nothing and am open to suggestions..

---

### Post by srs5694 on 2011-01-28
My best suggestion is to keep trying with TestDisk. It's got various levels of analysis, so if your initial attempt failed, tell it to look deeper (I don't recall the exact terminology it uses). You may luck out and find your partitions.

Failing that, you could convert the cylinder numbers in your fdisk output to sector values (there's a formula for doing this on the [Wikipedia entry for CHS](http://en.wikipedia.org/wiki/Cylinder-head-sector)). Then try rounding the values up or down to the nearest 1 MiB (2048-sector) boundary, since that's probably where the partitions began. Write a partition table using a guess and see if you can access it. If so, keep that setting (at least for the partition's start value; you might need to tweak the end point) and try again with the next partition. Ignore the swap partition; just do this for the NTFS and LVM partitions; then if you succeed in recovering the NTFS and LVM partitions, you can add a new swap partition -- but be sure you've got the NTFS partition's end point right before you add a new swap partition; if you've set the NTFS partition too small, this would damage the end of the filesystem!

Good luck! If you succeed (or if you don't and have to reinstall everything), you can create a backup of your partition table with:

```

sudo sfdisk -d /dev/sda > partitions.sda

```

---

### Post by psusi on 2011-01-28
> **nick55 said:**
> As mentioned above, I did delete the swap, but Ubuntu didn't want to start - it wanted to mount the swap partition and would hang if I just press "ENTER" to continue.


It should continue just fine without it, but if not, either recreate it with gparted as I said before, or remove it from /etc/fstab.

---

