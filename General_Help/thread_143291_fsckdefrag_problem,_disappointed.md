---
title: "fsck/defrag problem, disappointed"
date: 2006-03-12
forum: General Help
---

### Post by Gigante on 2006-03-12
Hi!

I recently installed Ubuntu, server only, no GUI. Intel CPU, No weird hardware, standard IDE drive. I also installed popfile and the pre-requisites Apache, Perl etc. Popfile has been running a few days.

Yesterday I thought I should check out the status of the disk. I installed defrag, tried to run it but was told: "Cannot work on a mounted device" which is kind of lousy. I have only one linux-partition, except for the swap partition. How am I supposed to defrag my disk???

Then I tried fsck, could not run at is it ALSO could not run on a mounted disk! What's up with that? I added a "read-only" option and made it run, producing the output seen below. Hey hey, I've had the system up and running a few days and there's already problems with the filesystem!? I am surprised and disappointed. Is this normal for linux? 
I guess it could be a problem with the disk or so, but I've been running Windows 2000 Server on it for months without any problems. I'm thinking of scrapping this and go back to Windows. Can't afford to take any risks with my data. Please advice.

nebol@plumbum:~$ sudo fsck -n
Password:
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Warning! /dev/hda7 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 1189827 has zero dtime. Fix? no

Inodes that were part of a corrupted orphan linked list found. Fix? no

Inode 1190070 was part of the orphaned inode list. IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (2330411, counted=2330374).
Fix? no

Inode bitmap differences: -1189827 -1190070
Fix? no

Free inodes count wrong (1226030, counted=1226015).
Fix? no


/: ********** WARNING: Filesystem still has errors **********

/: 28146/1254176 files (0.7% non-contiguous), 173713/2504124 blocks

---

### Post by kaamos on 2006-03-12
ext3/reiserfs disks do **not** need defragging. And trying that on mounted disks is a really bad idea..

---

### Post by Yagisan on 2006-03-12
[QUOTE=Gigante]Yesterday I thought I should check out the status of the disk. I installed defrag, tried to run it but was told: "Cannot work on a mounted device" which is kind of lousy. I have only one linux-partition, except for the swap partition. How am I supposed to defrag my disk???[/quote]
Linux filesystems do not need to be defraged. They are designed to resist fragmentation.

[QUOTE=Gigante]Then I tried fsck, could not run at is it ALSO could not run on a mounted disk! What's up with that?[/quote]It's trying to stop you from destroying your data. Heed it's advice. It can't say if a file is or is not corrupted if the file is open. Often a file is still open by a program, while it is indicated as deleted on the disk, eg a temporary file. To fsck that looks like an error, but when the program closes the file, it will be in a consistant state.

[QUOTE=Gigante]I added a "read-only" option and made it run, producing the output seen below. Hey hey, I've had the system up and running a few days and there's already problems with the filesystem!? I am surprised and disappointed. Is this normal for linux? [/quote]
And reading the error, it seems you actually had the condition it warns about. If you really want to force a check on your filesystems do this ```
sudo touch /forcefsck
```Then reboot the server, eg with ```
sudo shutdown -r now
```. The system will automatically check all disks on restart.

[QUOTE=Gigante]I guess it could be a problem with the disk or so, but I've been running Windows 2000 Server on it for months without any problems. I'm thinking of scrapping this and go back to Windows. Can't afford to take any risks with my data. Please advice.[/QUOTE]Read the message the tools give you! Defragmenting is not needed. Use a journalling filesystem (that's is anything except for ext2, if you left it at the default on install you have ext3), look at using a raid 1 or raid 5 setup, and backup backup backup.

Regards,
Yagisan

---

### Post by az on 2006-03-12
[QUOTE=Gigante]Can't afford to take any risks with my data. Please advice.

nebol@plumbum:~$ sudo fsck -n


/: 28146/1254176 files (0.7% non-contiguous), 173713/2504124 blocks[/QUOTE]


Well then don't run fsck on a mounted filesystem.  Also, unix is case-sensitive - did you mean to type fsck -N ?

Every time you boot, the kernel is loaded into memory along with a ram disk.  Your disk is not even mounted at that point, and fsck will be run every 30 times the disk is to be mounted.  

Ext3 is very very safe.  I wouldn't think of keeping the archive of my children's baby photos I have on anything other than an ext3 filesystem (other than a DVD....)

---

### Post by Gigante on 2006-03-12
Yagisan, thanks for the sudo touch /forcefsck advice, that was exactly what I was looking for! Will check it and return tomorrow with the results. :)

Yea I know ext2fs is supposed to auto-defrag, but I wanted to examine its efficiency for myself.

I'm kind of used to running chkdsk for error-checking and PerfectDisk for defragmenting in Windows, even on disks that are currently in full use by BitTorrent.. :) so not being able to do that in Linux felt like a let-down.

But if this boot-time-check takes care of the error-checking, and if the errors I had are actually just temporary-file problems like you said, and the auto-defragging works, then I'm all good! :)

azz, no I meant -n for read-only check. Specific option for the ext2fs version of fsck.

Thanks for all the info!

---

