---
title: "Files created in ubuntu are missing in win 7"
date: 2011-08-01
forum: General Help
---

### Post by ramitwadhwa on 2011-08-01
I have created 2 files and put them in a folder in ubuntu 11.04 64bit.  The partition is ntfs and is shared b/w ubuntu and win7. The partition  doesnot have win7 installed on it,  win7 ubuntu and data partition are  three seprate partitions of a disk. when i logged in win7 the files and  folder newly created were missing. then i logged back in ubuntu and they  were missing from there to.

I have edited /etc/fstab => 
"# data Drive
UUID=C8E8EC38E8EC2682 /media/data ntfs auto 0 1" 
so that the partition  mounts itself at boot up, thats it I do not specifically unmount it, i  just shutdown the pc normally. also win7 is hibernated, but its on sda0  its a different partition.

---

### Post by xdragonforce on 2011-08-01
Whoa whoa whoa!
How did you install Ubuntu onto an ntfs partition?
Ubuntu only works on ext and / based filesystems.

---

### Post by aeiah on 2011-08-01
are you sure the device is mounting to /media/data? ie, can you see files you create in windows 7 on there?

oh, and to clarify for xdragonforce: the user has 3 partitions - windows, ubuntu, and data. data is an ntfs partition and saving files to it under ubuntu doesn't seem to be persistent

---

### Post by ajgreeny on 2011-08-01
If your Win7 is hibernated and not totally shutdown, the partitions that it was using will still probably be flagged as "in use" and therefore not available for another OS to read or write to.

If you are moving from one OS to the other, but with shared partitions which both OSs can read and write, you **must** completely shutdown the running OS first.  In fact I'm surprised that you can boot to one whilst the other is only hibernated.

Sorry if I misunderstood, but that is how it reads to me.

---

### Post by Mark Phelps on 2011-08-01
If the shared drive was open when Win7 was running, when you hibernated it, it made a copy of the partition table.  When your restarted it, it overwrote the new table with the old.

It's a BAD idea to make ANY changes to shared NTFS partitions while Windows is Hibernated.

---

### Post by ramitwadhwa on 2011-08-01
> **xdragonforce said:**
> Whoa whoa whoa!
How did you install Ubuntu onto an ntfs partition?
Ubuntu only works on ext and / based filesystems.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       17526   110061284+   f  W95 Ext'd (LBA)               (WINDOWS 7)
/dev/sda3           17527       19336    14535680   83  Linux                               (UBUNTU)
/dev/sda4           19336       19458      975872   82  Linux swap / Solaris           (SWAP)
/dev/sda5            3825       17526   110061283+   7  HPFS/NTFS                     (DATA)

---

### Post by Mark Phelps on 2011-08-01
OK ... so that confirms that you have separate partitions for Win7, Ubuntu, and your data -- but it is STILL a bad idea to write to the shared NTFS partition while Windows is hibernated.

---

### Post by ramitwadhwa on 2011-08-02
> **Mark Phelps said:**
> OK ... so that confirms that you have separate partitions for Win7, Ubuntu, and your data -- but it is STILL a bad idea to write to the shared NTFS partition while Windows is hibernated.

please give some suggesstion what to do.
I have edited /etc/fstab => 
"# data Drive
UUID=C8E8EC38E8EC2682 /media/data ntfs auto 0 1" 
so that the partition  mounts itself at boot up, thats it I do not specifically unmount it, i  just shutdown the pc normally. also win7 is hibernated, but its on a different partition.

---

### Post by Mark Phelps on 2011-08-02
> **ramitwadhwa said:**
> please give some suggesstion what to do.

As long as you continue to (1) use the shared data partition in Win7 and (2) hibernate Win7 -- you will continue to have this problem.

You can't fix this from Linux because Win7 is always going to overwrite the shared data partition table when you resume it from hibernation.

To do what you want (make changes to the shared NTFS partition while in Ubuntu), you have to SHUT DOWN your Win7 session, restart your PC, and THEN boot into Ubuntu.

---

### Post by ajgreeny on 2011-08-03
Thanks Mark.

It sometimes seems as if we talk to brick walls, giving advice which is then ignored, and I was beginning to think my comments in post 4 were wrong.

However, it is a long time since I had a dual boot with windows, so thought things might have changed.  I have also not used Win7, so don't know if it set like Vista, that is, to suspend or hibernate, and not shutdown properly, as the default.   It took me a while to notice that on my wife's Vista laptop.

Ghastly OS was Vista!!  Laptop now with 10.04, thank goodness.

---

