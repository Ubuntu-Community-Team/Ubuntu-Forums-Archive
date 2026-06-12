---
title: "Power cut while repartitioning - how to repair?"
date: 2012-07-18
forum: General Help
---

### Post by Xero Xenith on 2012-07-18
OK, it wasn't a power cut. It was a vicious attempt at sabotage by someone else in the household. (Why would you do such a thing?) Anyway, here's my situation.

I was moving my "data" partition - which contains no system files - leftwards to make full use of the hard drive it's on, increasing it from 1.2 TB to 1.5 TB. About midway through, the power cable was yanked, so I'm left with a 1.5 TB partition that actually mounts fine, but only contains 1.2 TB of data and a few hundred MB of free space. Clearly this is wrong - there should be a few hundred GB.

I'm wondering if there's a way to either continue the operation where it left off, or to check the disk thoroughly and repair it to a good state. fsck finishes in less than a second and reports:

```
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sdb4: clean, 276060/80871424 files, 303409144/323478815 blocks
``` 

All the data is backed up, so I can restore, but I'd rather not as my backup drives are slow and it could even take days. Any opinions/suggestions would be really, genuinely appreciated :)

---

### Post by Primefalcon on 2012-07-18
I'd recommend giving testdisk a spin

---

### Post by Xero Xenith on 2012-07-18
> **Primefalcon said:**
> I'd recommend giving testdisk a spin

Thanks for the reply. I'm running it now but don't know what to do exactly - I'm just running the default scan (which I think is actually searching for lost partitions). I'll scout around the menus for a way to fix an ext4 partition. Thanks for the suggestion :)

EDIT: do I want to do this?
```
 To repair the filesystem using alternate superblock, run
>fsck.ext4 -p -b superblock -B blocksize device   
```
                             
I have no idea what a superblock is... wiki time!

[snip]

Edit 5: OK, now we're seeing some of that lovely corruption it seems.

```
ubuntu@ubuntu:~$ sudo fsck.ext4 -p -b 32768 -B 4096 /dev/sdb4 
/dev/sdb4: One or more block group descriptor checksums are invalid.  FIXED.
/dev/sdb4: Group descriptor 0 checksum is invalid.  

/dev/sdb4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
ubuntu@ubuntu:~$ 
```

Unexpected considering all fsck scans I do come back with no errors. How can I force a complete filesystem check (ext4)?

Edit again: tried
```
sudo fsck -pvcf /dev/sdb4
```, which came back with the exact same output as the above. It really hates this filesystem :P

Edit: Tried the same as above without -p, it's fixed the "Group descriptor checksums" up to 9871. Seems like they were all corrupted to 9871. Now checking for bad blocks.

---

### Post by Cheesemill on 2012-07-18
You would be better off just recreating the partitions and restoring from backup.

A power failure during a gparted operation is more than likely going to screw up your system beyond all hope of recovery.

---

### Post by epikvision on 2012-07-18
It seems like starting from scratch with your partitions.

---

