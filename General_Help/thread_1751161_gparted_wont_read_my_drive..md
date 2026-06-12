---
title: "gparted wont read my drive."
date: 2011-05-06
forum: General Help
---

### Post by Meow27 on 2011-05-06
So I got my new SSD. and i reimaged my windows 7 partitions into the drive.

It seems that Acronis Isn't the greatest Image restorer, and, well From what i understand, both of my partitions overlap. 
```
sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000307ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             155        7012    55082160    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7012       14593    60895769+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3   *           1         156     1239808+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5            7012       13461    51801088+  83  Linux
/dev/sda6           13461       14332     6992968+   7  HPFS/NTFS
/dev/sda7           14332       14593     2101648+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

What do i do to fix partitions 1,2,3?

thanks in advance

---

### Post by satanselbow on 2011-05-06
This is something that came up the other day - for a different reason ;)

The "cylinder" error is where your original windows installation created the partition - this error was not created by Acronis and it just did what is was told - and the Extended partition was created by a windows tool as well?

Are you trying to use gparted from a LiveCD or are you booting the disk and running gparted from the working installation? 

Are the W7 and Linux installations booting at all?

---

### Post by Rubi1200 on 2011-05-06
Please also run the following 2 commands and post the output, wrapping with code tags as before:

```
sudo fdisk -lu

sudo sfdisk -V
```

---

### Post by Meow27 on 2011-05-06
> **satanselbow said:**
> This is something that came up the other day - for a different reason ;)

The "cylinder" error is where your original windows installation created the partition - this error was not created by Acronis and it just did what is was told - and the Extended partition was created by a windows tool as well?

Are you trying to use gparted from a LiveCD or are you booting the disk and running gparted from the working installation? 

Are the W7 and Linux installations booting at all?
yes both partitions are booting.

I originally installed linux and had it working perfectly fine. (_both windows and linux function perfectly!_ partition managers have similar problems that gparted does though (like paragon))
Then when i got the tools, I burned an image of the windows 7 partitions from my old disk onto the drive.

Since this is an SSD its ludicrous to say, but I set all my linux stuff to the right, and windows to the left

And I deliberately made my linux partitions inside an extended one.


> **Rubi1200 said:**
> Please also run the following 2 commands and post the output, wrapping with code tags as before:

```
sudo fdisk -lu

sudo sfdisk -V
```

```
sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000307ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         2479680   112643999    55082160    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       112644061   234435599    60895769+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       15120     2494736     1239808+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5       112644063   216246239    51801088+  83  Linux
/dev/sda6       216246303   230232239     6992968+   7  HPFS/NTFS
/dev/sda7       230232303   234435599     2101648+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
```
sudo fdisk -V
fdisk (util-linux-ng 2.17.2)

```

---

### Post by Quackers on 2011-05-06
As far as I can see the only partitions that overlap are sda3 and sda1.
For some reason sda3 starts at sector 1 (which I think is wrong nowadays) and finishes at sector 156.
Sadly sda1 starts at sector 155, hence the problem.
Why is sda3 physically on the disc before sda1? Do you know?
What is in sda3 and what size is it, 75MB?

---

### Post by srs5694 on 2011-05-06
> **Quackers said:**
> As far as I can see the only partitions that overlap are sda3 and sda1.
For some reason sda3 starts at sector 1 (which I think is wrong nowadays) and finishes at sector 156.

Actually, those are *cylinder* values, not *sector* values. The fdisk output in post #4 shows the sector values. Your conclusion that only partitions 1 and 3 overlap is correct, though, unless I too missed something.

There is another problem, though: SSDs have alignment issues similar to those of Advanced Format disks and RAID arrays. I'm foggy on the details, and I don't know how big the performance hit is for misalignment, but I'm pretty sure that most work best with some power-of-2 alignment in the 32 KiB (64-sector) to 1048 KiB (1 MiB; 2048-sector) range. Partition 1 aligns to a 64-sector boundary, 2 doesn't matter because it's an extended partition, 3 aligns to a 16-sector boundary, and 5, 6, and 7 are all odd and so align to 1-sector boundaries. Thus, most of these partitions are likely to experience degraded performance. You'll have to check with the drive's manufacturer to be sure if it's got such alignment issues, and if so, what the optimum alignment is.

My recommendation is to back up *all* of this disk's data, create new partitions on 1 MiB boundaries, and restore the data to these partitions that you create manually. I'm not familiar with the Acronis software you mention, Meow27, so I can't say whether it will do the job. I've used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) under Windows to back up and restore Windows partitions in the past. It's a file-based solution, so you can (and must) create partitions outside of that software to do the restores. Under Linux, I personally would use tar, but there are other tools that will work.

As for partitioning, you can use a *recent* version of GParted (be sure it's recent enough to offer a 1 MiB alignment option) or use fdisk with sector-precise measurements (the default cylinder precision is worse than useless) and check the partition start values manually -- divide any value by 2048 (or whatever sector alignment value you use) and see if it's a whole number. If it is, you're fine. If not, the partition is misaligned.

---

### Post by Quackers on 2011-05-07
oops, my bad.

---

### Post by Meow27 on 2011-05-07
> **srs5694 said:**
> Actually, those are *cylinder* values, not *sector* values. The fdisk output in post #4 shows the sector values. Your conclusion that only partitions 1 and 3 overlap is correct, though, unless I too missed something.

There is another problem, though: SSDs have alignment issues similar to those of Advanced Format disks and RAID arrays. I'm foggy on the details, and I don't know how big the performance hit is for misalignment, but I'm pretty sure that most work best with some power-of-2 alignment in the 32 KiB (64-sector) to 1048 KiB (1 MiB; 2048-sector) range. Partition 1 aligns to a 64-sector boundary, 2 doesn't matter because it's an extended partition, 3 aligns to a 16-sector boundary, and 5, 6, and 7 are all odd and so align to 1-sector boundaries. Thus, most of these partitions are likely to experience degraded performance. You'll have to check with the drive's manufacturer to be sure if it's got such alignment issues, and if so, what the optimum alignment is.

My recommendation is to back up *all* of this disk's data, create new partitions on 1 MiB boundaries, and restore the data to these partitions that you create manually. I'm not familiar with the Acronis software you mention, Meow27, so I can't say whether it will do the job. I've used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) under Windows to back up and restore Windows partitions in the past. It's a file-based solution, so you can (and must) create partitions outside of that software to do the restores. Under Linux, I personally would use tar, but there are other tools that will work.

As for partitioning, you can use a *recent* version of GParted (be sure it's recent enough to offer a 1 MiB alignment option) or use fdisk with sector-precise measurements (the default cylinder precision is worse than useless) and check the partition start values manually -- divide any value by 2048 (or whatever sector alignment value you use) and see if it's a whole number. If it is, you're fine. If not, the partition is misaligned.

in short, nuke the drive and start from scratch?
my SSD is an intel x-25M 120 GB silver if that explains anything

*sighs* suppose ill have to go down that road.

---

