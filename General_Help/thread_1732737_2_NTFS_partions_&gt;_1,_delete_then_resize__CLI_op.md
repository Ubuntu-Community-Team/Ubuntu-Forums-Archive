---
title: "2 NTFS partions &gt; 1, delete then resize?  CLI options?"
date: 2011-04-18
forum: General Help
---

### Post by iconoclast hero on 2011-04-18
Disk:
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   307194929   153597433+   7  HPFS/NTFS
/dev/sdb2       307194930   312576704     2690887+   7  HPFS/NTFS
```Device was from a USB drive and the USB controller went, so it was probably not bootable anyway.  It has my music other data on it and is about full so I want to take the empty space from sdb2 and add it to sdb1.  Currently it is mounted as /media/windows and /media/windowsh (as this was my H partition).  As you can see it was NTFS and was used on my XP box.  Presently it is inside my headless 10.10 server so booting from a gparted live cd is less preferable than going in via SSH from another terminal.  

That leads me to my next question, if I have unallocated space do I then need to go in with fdisk and ntfsresize?  I am a little confused about what I read concerning that...

Is there a way to get at a remote drive with gparted?

Is this really as simple as fdisk /dev/sdb  >> u  >>  d >> partition 4 and then resizing the partition?  I'm trying to figure the best route to go and most people have problems like, "I can't clear off the partition easily" or "I want to keep a windows partition to dual boot" so I haven't been able to find my question asked. 

Again, the preferable solution would be to not have to physically move KVM or the box to where the other is.

---

### Post by iconoclast hero on 2011-04-20
Can anyone point out the correct way to do this?

---

### Post by Mark Phelps on 2011-04-21
Personally, I would not trust any command to merge partitions without suffering data loss. 

I think you'll just have to go through the painful and tedious process of moving files from one partition to another, resizing the partions, moving again, resizing again -- until you get all the files moved and can then remove the originating partition and resize the destination partition.

---

### Post by iconoclast hero on 2011-04-21
> **Mark Phelps said:**
> Personally, I would not trust any command to merge partitions without suffering data loss. 

I think you'll just have to go through the painful and tedious process of moving files from one partition to another, resizing the partions, moving again, resizing again -- until you get all the files moved and can then remove the originating partition and resize the destination partition.

Thank you for the reply Mark, but I think you misunderstood.  I'm at the point where I have the small partition I want to remove empty.  There is no need to move and resize.  My question is, now that I'm at this point, do I delete the partition and then resize into unallocated space?  What tools should I use to do this from the command line?

---

