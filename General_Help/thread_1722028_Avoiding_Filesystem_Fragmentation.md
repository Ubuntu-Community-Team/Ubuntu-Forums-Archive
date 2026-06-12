---
title: "Avoiding Filesystem Fragmentation"
date: 2011-04-05
forum: General Help
---

### Post by Fishbowler on 2011-04-05
I keep 2 drives for data storage in my box.

One is a dumping ground for everything new. It's easy to access from other places via samba, etc, but isn't permanent. 
The second drive has an actual system of folders.

Every once in a while, I grab groups of files from drive 1 and copy them into the appropriate folder in drive 2, then delete the originals. Depending on how long I've left it, each copy can be pretty lengthy.

Currently, I sit patiently waiting for one copy to end before I kick off the next one.

Here comes the first question: In my youth, I was taught not to do concurrent copying because FAT32 would get all fragmented. Is this still the case with ext3?

There are articles about, like [this one]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting"), which explain why fragmentation is more difficult to achieve under ext3, especially for disks under 80% utilised. My second disk is around 98% utilised, but that's an entirely different problem!

If fragmentation really isn't a problem, how about a performance cost in writing to multiple physical disk locations?

All told - am I being crazy waiting?

If not, I take it there's no way to queue file transfer jobs?

---

### Post by vanadium on 2011-04-05
Fragmentation should not be an issue of practical importance on drives that have enough space left. I would not worry.

---

### Post by searchfgold6789 on 2011-04-05
In ext2,3,4 filesystems fragmentation should not even be a problem at all. For faster file transfers, try making the data on the FAT32 filesystem be on an ext3/ext4 one instead.
As for queuing file transfers, my favorite way to do this is to use the good old terminal. The utility for copying files and other things is [FONT=Courier New]cp[/FONT]. Here is an example of a script that copies files from one point to another several times. It's not very good but it's what I can come up with.
```

cp -r -v /media/XP/cdrive /media/linux/home/user/Backup
cp -r -v /media/XP/Photos /media/linux/home/user/Backup/Photos
cp -v /media/linux/setups/java.bin ~/Downloads/jre.bin

```You could also just copy all of them at the same time, which would work pretty well if you had, like, a multiple-core CPU that isn't doing much else.

---

