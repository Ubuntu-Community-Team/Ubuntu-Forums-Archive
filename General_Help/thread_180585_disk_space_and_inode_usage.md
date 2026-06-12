---
title: "disk space and inode usage"
date: 2006-05-22
forum: General Help
---

### Post by diff_sky on 2006-05-22
Hi,

I'm having a problem with the amount of disk space being reported on my system (but the problem may just be my lack of knowledge!)

I have a raid 5 setup ([details here]("http://www.ubuntuforums.org/showthread.php?t=167058")) on which I have an ext3 filesystem ontop of lvm.

Output of mdam dev/md0:
```

matthew@mammatus:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Thu Apr 27 00:56:00 2006
     Raid Level : raid5
     Array Size : 586099200 (558.95 GiB 600.17 GB)
    Device Size : 293049600 (279.47 GiB 300.08 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May 22 20:16:14 2006
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2e763809:706de222:4bc3704d:083e37dc
         Events : 0.24274

    Number   Major   Minor   RaidDevice State
       0      33        1        0      active sync   /dev/hde1
       1      34        1        1      active sync   /dev/hdg1
       2      56        1        2      active sync   /dev/hdi1

       3      57        1        -      spare   /dev/hdk1

```
so you can see the disk should be 558G

But here's the output of df -h:
```

matthew@mammatus:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvm-root   25G  1.8G   22G   8% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hda1             221M   12M  198M   6% /boot
/dev/mapper/lvm--raid-home
                      551G   61G  462G  12% /home

```
551G!  (so lost 7G??)

After installing xdiskusage I can see that 27.95G is being consumed by **inodes**. I believe inodes are used as part of storing the actual data on the disk (is this correct)? They seem to be taking up a large amount of my disk - my question is: is that right?? If not, what can I do about it?

Confused.

Thanks for any help.

---

### Post by Fatjoint on 2006-05-22
Just a guess and I may be completely off base here but -

If I remember correctly, files cannot share the same inode across different hardware.  So, is it possible that some files are duplicated in their entirity across the seperate volumes while the others are checksum'd?

If that's true, then what characteristic exactly is the determining factor in whether a file is mirrored or striped+checksum?

---

### Post by diff_sky on 2006-05-23
I've no idea on that :(

Anyone else got any clues, is this inode space correct?

---

### Post by drl on 2006-05-23
Hi,  diff_sky.

The man page for mkfs.ext2 has 3 basic choices for the inode to data block ratio:
```
news        one inode per 4kb block
largefile   one inode per megabyte
largefile4  one inode per 4 megabytes
```
However, I don't know how that might interact with a RAID.  Suppose you didn't have RAID, does the ratio make sense?

There is a good article for inode background at [http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

Best wishes ... cheers, drl

---

### Post by diff_sky on 2006-05-23
thanks drl,

I read somewhere that the ext3 filesystem uses about 5% of the capacity to file system overhead.

5% of 558G is 27.9G - and this is the size of the inodes being reported, so that ratio makes sense. But that maeks sense against the 558G not the 551G  reported.

Ah well, I gues 523G is enough really... :)

---

### Post by drl on 2006-05-23
Hi, diff_sky.

Do you think the difference could be in the use of 1000 vs 1024, and 1000**2 vs 1024**2?  I've often been caught by that.  Otherwise, for a journaled FS, there may be some additional overhead, but I don't know enough to be able to say more than just that.  Beyond those two thoughts I would need other comments ... cheers, drl

---

### Post by diff_sky on 2006-05-23
hmmm could be, my brain hurts at the moment to calculate it :)

what's 1000**2 / 1024**2?

---

### Post by drl on 2006-05-23
Hi, diff_sky.

That's how many programming languages express the square of a number, so 1000**2 -> 1000*1000 ->1,000,000, and 1024**2 -> 1,048,576.

So a "K" could be 1000 or 1024, and an "M" could be 1,000,000 or 1,048,576.

Apologies for the confusion  ... cheers, drl

---

