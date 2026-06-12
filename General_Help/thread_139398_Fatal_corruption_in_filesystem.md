---
title: "Fatal corruption in filesystem"
date: 2006-03-04
forum: General Help
---

### Post by Grey on 2006-03-04
I have an old Pentium 233 that I use as a file server/web server/subversion server.  It has always done its job well... but I did a kernel update on it a few days back, and it never came back up.  I plugged a monitor and keyboard into it to see what was the matter, and it gives me this:

```

* Checking all file systems...
/boot: clean 34/48192 files, 25162/96390 blocks
Reiserfs super block in block 16 on 0x345 of format 3.6 with standard journal
Blocks (total/free): 69595584/33481519 by 4096 bytes
Filesystem is clean
Filesystem seems to have fatal corruptions.  Running with --rebuild-tree is required.
/opt: clean, 39/490560 files, 81883/979933 blocks
/tmp: clean, 12/977032 files, 155619/1951866 blocks
/usr: clean, 11726/366528 files, 70568/732965 blocks
/usr/local: clean, 23/977032 files, 155629/1951866 blocks
/var: clean, 1572/366528 files, 64979/732957 blocks
   ...fail!

* fsck failed.  Please repaid manually

* CONTROL-D will exit from this shell and continue system startup.

```

Problem is... I've never repaired a filesystem manually before, and I have no idea how to do that.  Any ideas anyone?  Thanks in advance.

---

### Post by stuporglue on 2006-03-04
Well, does CONTROL-D actually get the system booted up? That's what I'd try first. 

If it doesn't, type your password, then run 

fsck.$FSTYPE /dev/$PARTITION

where $FSTYPE is ext3, ext2, reiserfs or whatever your filesystem is, and $PARTITION is the partition you want to check. If you're lucky, it'll go well, if not hope you have everything backed up, and answer the questions to the best of your ability. 

Data that's in the wrong place (bad inode messages etc.) that ask if they should be moved/repaired end up in /lost+found of that partition, assuming the partition ends up being mountable. :-D 

BTW. Even if the disk does come back up, I recomend getting anything you don't have backed up off of it, and doing a new format/install. It is also *possible* that the disk is dying, so keep good backups till you trust the disk again. 

Good luck!

---

### Post by Grey on 2006-03-04
Thanks a lot.  I will try that right away.  I tried mounting the partitions that didn't mount earlier, and things seem to be in working order... but the error REALLY scares me.  The hard drive that my home partition resides is a 300GB drive that's only a couple of months old though... so I'm pretty sure that my relevant data is safe.  However, the 15GB drive that the OS resides on is fairly old, and could very well be dying, so I will take your suggestion under advisement.  (Is there any tool to check drive health?)

Anyway, here goes.  Thanks again for your quick and helpful advice.

EDIT:  fsck worked, but still told me that I had to --rebuild-tree on my /home partition... which means it's the last time I am likely to use reiserfs.  I am going to spend tomorrow trying to backup all the data, and then --rebuild-tree.  This just shouldn't be happening.  But thanks again.  I know what I need to do now.

---

### Post by akiro.yamamoto on 2006-03-04
I had this error, when I specified Reiserfs but the partition is actually ext3, check the fstab entry for the affected partition.
I only realised this error because I had both SUSE and Ubuntu installed, the Ubuntu
booted up properly and mounted the partition, the SUSE gave me errors.
This may not be your situation, but bear it in mind. 
;)

---

