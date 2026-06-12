---
title: "Hard Drive not found in terminal"
date: 2011-05-30
forum: General Help
---

### Post by rasmukri on 2011-05-30
So I have a hard drive with about 700 gb of movies on it and i plugged it in via USB and it didn't show up anywhere. So i then tried to plug it into the computer any way i could finally i tired another external case and now it is found (sorta).  I open my /media folder and there it is a drive labeled Movies it had an x and it said i couldn't open it no permissions so i added permissions. now i open it and it says no files but only 160 gb space remaining on a 1 tb drive.  so when i run fdisk -l i get this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfeb3feb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       18970       19458     3916800   82  Linux swap / Solaris
/dev/sda2            3648       18970   123076609    5  Extended
/dev/sda5            3648       18970   123076608   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT

```

i have 2 each 2 tb drives internally in the computer that are fine and a 160gb drive for the main Ubuntu system but i cant find my movies drive so when i try to run any program for recovery it cant find anything to fix because it isn't there. i ran testdisk and gpart but they only show what i am not looking for.
How do i make the computer find the drive or even just copy the files off it to another drive?
Thanks

---

### Post by katykat on 2011-05-30
The first thing I woudl do it take it to Windoze and enable full r/w on the drive. That *should* set the CACLS permissions. 

If ti still dont work i would boot up to a Meerkat or Lucid LiveCD and see if any of THOSE recognize the external drive correctly. 

I assume you are running Natty.
Then test with the Natty LiveCD. 

If the earlier ones work, and the Natty CD does not - it may be a bug.

If the Natty CD works, then something hosed your hardware recognition daemons - Amavis?? and some others.... Hopefully someone a little more knowlegeable will jump in.

The problem I am having is getting Samba to access the Tb external when its on the Win machine. Works OK when its plugged directly in.

---

### Post by rasmukri on 2011-05-30
> **katykat said:**
> The first thing I woudl do it take it to Windoze and enable full r/w on the drive. That *should* set the CACLS permissions. 


when i plug it into windows it is unrecoginized it shows up nowhere on XP or on win 7

ill try the live CD's and see how that works.
i have plugged it directly into the computer and that didnt work the computer hung at the bios boot.

---

### Post by rasmukri on 2011-05-30
no go on any of the older versions i tried 9.04 through 11 and no luck on getting it to see the drive.  it is also making a strange noise when i turn the drive on  i think it could be actually broken and in need to be sent to a data recovery place.

---

