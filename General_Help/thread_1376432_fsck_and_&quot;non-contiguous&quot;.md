---
title: "fsck and &quot;non-contiguous&quot;"
date: 2010-01-09
forum: General Help
---

### Post by CharlesA on 2010-01-09
Hi all,

I ran fsck on  one of my backup drives, one that is almost full, and I'm not quite sure if that drive is going bad or not.

It's running ext3 and has around 1.6TB used (2.0TB drive).

This is what the output was:

```
charles@thor:~$ sudo fsck -rV /dev/sdc1
fsck from util-linux-ng 2.16
[/sbin/fsck.ext3 (1) -- /dev/sdc1] fsck.ext3 -r /dev/sdc1
e2fsck 1.41.9 (22-Aug-2009)
DVDs_Backup has been mounted 42 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes


Pass 4: Checking reference counts
Pass 5: Checking group summary information

DVDs_Backup: ***** FILE SYSTEM WAS MODIFIED *****
DVDs_Backup: 8459/122101760 files (**32.7% non-contiguous**), 376193806/488378000 blocks

```

It should say "clean" right?

There isn't anything in the lost+found directory.

Also, when should I be running fsck on these drives, since they are backups and are mounted every hour, then unmounted.

Thanks.

EDIT: Ran fsck on my regular backup drive and the results were more normal:

```
charles@thor:~$ sudo fsck -rV /dev/sdd1
[sudo] password for charles:
fsck from util-linux-ng 2.16
[/sbin/fsck.ext3 (1) -- /dev/sdd1] fsck.ext3 -r /dev/sdd1
e2fsck 1.41.9 (22-Aug-2009)
Docs_Backup has been mounted 270 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

Docs_Backup: ***** FILE SYSTEM WAS MODIFIED *****
Docs_Backup: 30283/91578368 files (1.5% non-contiguous), 48010117/366284000 blocks

```

I found some info about how ext3 defrags itself and that it cannot handle large files very well. [Source.]("http://ubuntuforums.org/showthread.php?t=547618")

Kinda makes me wonder how badly fragmented my 4TB partition is going to be. >.<

---

### Post by kidders on 2010-01-10
Hi there,

> **CharlesA said:**
> when should I be running fsck on these drives, since they are backups and are mounted every hour, then unmounted.You may want to use tune2fs to bump the mount count threshold up to something sensible, given the frequency with which you mount the filesystem. You *do* need to run fsck every now and then ... but probably no more frequently than, say, once a month at the most.

> **CharlesA said:**
> I ran fsck on  one of my backup drives, one that is almost full, and I'm not quite sure if that drive is going bad or not.fsck can't tell you if a drive is going bad ... its function is to determine if the filesystems *on* a drive are consistent or not. To determine how close the disk itself is to failure, you'd need to monitor its SMART status over a period of time.

There are two issues with the output you posted...[LIST=1]
[*]The filesystem is pretty badly fragmented, something that's bound to happen faster than normal on a backup disk. It's not worth addressing unless you *feel* it's worth addressing ... for example, if the filesystem's performance has degraded significantly enough to be noticeable.
[*]fsck doesn't like it if a filesystem is modified while it's examining it. In your case, it had to re-create /lost+found (presumably because you'd deleted it), which (obviously) requires filesystem modification, so fsck can't say for sure it's clean. To be certain, you might like to run fsck again.
[/LIST]

> **CharlesA said:**
> I found some info about how ext3 defrags itself and that it cannot handle large files very well.It's not strictly true to say Ext3 defragments itself (some filesystems do try), but it is pretty good at *resisting* fragmentation. That said, as a filesystem fills up, large files become basically impossible to handle "well", because it gets progressively harder to find a way to store them contiguously. Backups typically consist of lots of big tarballs on a relatively full filesystem, that're constantly being added & deleted, and tend to grow over time ... a perfect recipe for fragmentation on almost any filesystem. Unless the degree of fragmentation gets disastrously bad, or you start to get worried about the sheer amount of thrashing your disk has to do to read the filesystem, it's not a cause for concern.

Mind you, your tolerance for fragmentation on, say, your root filesystem should be much lower, because the performance of your entire system depends on it being well-tuned.

I hope that helps.

---

### Post by CharlesA on 2010-01-10
Thanks for the info!

I haven't run fsck on my root partition in a while (mostly since I'd need to boot from a livecd or run "touch /forcefsck"), so I don't know how much non-contiguous files it's got but since it's only got around 1.5GB of used space, it shouldn't be too bad.

On the 4TB partition, I think it was something along the lines of 8% non-contiguous, which isn't that bad.

I'll think that I'll install smartmontools on the box and have it check the drives every 2 weeks or something.

Thanks again!

---

### Post by dcstar on 2010-01-11
> **CharlesA said:**
> 
.........
I'll think that I'll install **smartmontools** on the box and have it check the drives every 2 weeks or something.


Which will check the physical sectors on the drive and has absolutely nothing to do with the filesystem structure at all.

---

### Post by kidders on 2010-01-11
Yep... That's exactly the point. At filesystem level, it's tough to tell if the hardware is in good condition. Smartmontools will do a much better job than fsck.

---

### Post by CharlesA on 2010-01-11
> **dcstar said:**
> Which will check the physical sectors on the drive and has absolutely nothing to do with the filesystem structure at all.

Which is why I'll be running fsck about every month, and smartctl every 2 weeks.

> **kidders said:**
> Yep... That's exactly the point. At filesystem level, it's tough to tell if the hardware is in good condition. Smartmontools will do a much better job than fsck.

Sounds like it. Thanks again. :)

---

