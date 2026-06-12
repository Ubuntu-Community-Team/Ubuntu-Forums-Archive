---
title: "Backing up / to external disk"
date: 2009-11-16
forum: General Help
---

### Post by jhann on 2009-11-16
Hello,

I recently got an external hard disk that I'd like to back my ubuntu install onto.
I've formatted it using gparted and it's not ext4 format, now i've been looking around - some people suggest using tar but I want to be able to book off of it if my main disk fails.

I'm happy to zip my information (video, music) into a tar ball as that's alright. I've had a look and found I could use cpio, i've been trying:

find / -mount -print | cpio pdm /toshiba

I've mounted /dev/sdc1 as /toshiba.

I'm really new to this and can't find anything with the search function about it. Any recommendations?

---

### Post by Giblet5 on 2009-11-16
I use tar because:

It is available on every system. (cpio is optional on many systems)
It compresses like it's 1999.
WinZip and WinRar can both read them directly.

Let's say your external drive mounts to /media/USBdrive. This will back up your stuff perfectly and with good compression:

```
sudo tar -czpvf /media/USBdrive/backup.tar.gz /home
```


To restore that backup:

```
cd /
sudo tar -xzpvf /media/USBdrive/backup.tar.gz
```

---

### Post by blueridgedog on 2009-11-16
I use rsync, so that changes made to the source can be added incrementally to the targe rather than re-writing the entire backup.
```

rsync -av / /toshiba --delete --log-file=/home/USER/Desktop/$(date +%Y%m%d)_rsync.log --exclude 'toshiba'
```

Change USER as needed.

---

### Post by Giblet5 on 2009-11-16
> **blueridgedog said:**
> I use rsync, so that changes made to the source can be added incrementally to the targe rather than re-writing the entire backup.
```

rsync -av / /toshiba --delete --log-file=/home/USER/Desktop/$(date +%Y%m%d)_rsync.log --exclude 'toshiba'
```

Change USER as needed.

+1... but rsync won't work to a FAT32 or NTFS disk drive. Those filesystem types don't preserve permissions, ownership, or timestamps.

OP is using an external disk drive, unknown filesystem type (will wager FAT32), so rsync won't work.

---

### Post by ajgreeny on 2009-11-16
> **Giblet5 said:**
> +1... but rsync won't work to a FAT32 or NTFS disk drive. Those filesystem types don't preserve permissions, ownership, or timestamps.

OP is using an external disk drive, unknown filesystem type (will wager FAT32), so rsync won't work.
Agreed, but why not format it, or a partition on it to ext3 or ext4, then all will work great.  I think rsync is the way, but that's just a personal preference.  It's what I use to backup my home often as it is incremental.

---

### Post by Giblet5 on 2009-11-16
> **ajgreeny said:**
> Agreed, but why not format it, or a partition on it to ext3 or ext4, then all will work great.  I think rsync is the way, but that's just a personal preference.  It's what I use to backup my home often as it is incremental.

That is a good way to do a **partial** backup.

The rsync command doesn't preserve symbolic links, and the command as given above won't even preserve permissions or timestamps. Why even bother.

The options for performing a full backup are tar and cpio, plus some other off the wall products. One of those, zoo, will work very well also, and it has built-in version control!

Don't get me wrong, I use rsync every day. I love rsync. I want it to have my babies. But it's not a very good backup program, and it doesn't work at all on NTFS or FAT32 - filesystems that people frequently use. The tar and cpio commands don't care about filesystem type, so long as the fielsystem supports the Very Large Files that a backup can, and will, create (FAT32 is limited to 4G or less).

---

### Post by ajgreeny on 2009-11-16
> **Giblet5 said:**
> That is a good way to do a **partial** backup.

The rsync command doesn't preserve symbolic links, and the command as given above won't even preserve permissions or timestamps. Why even bother.

The options for performing a full backup are tar and cpio, plus some other off the wall products. One of those, zoo, will work very well also, and it has built-in version control!

Don't get me wrong, I use rsync every day. I love rsync. I want it to have my babies. But it's not a very good backup program, and it doesn't work at all on NTFS or FAT32 - filesystems that people frequently use. The tar and cpio commands don't care about filesystem type, so long as the fielsystem supports the Very Large Files that a backup can, and will, create (FAT32 is limited to 4G or less).
Agreed again, but I didn't notice the actual command used, just the suggestion for rsync.  When I use it I always use the options to preserve permissions, timestamps, groups and several others I can't remember at the moment.  It is fast, incremental, and for a backup of home files (a partial backup as you call it) it is everything I need.  I'm not even too worried about most of the hidden config folders, except for .mozilla and .mozilla-thunderbird, and some others that contain user files such as .purple (pidgin chat data) as it is so easy to sort out the application configurations from new when I update to a new ubuntu version.

---

### Post by blueridgedog on 2009-11-16
> **Giblet5 said:**
> rsync won't work to a FAT32 or NTFS disk drive. Those filesystem types don't preserve permissions, ownership, or timestamps.

OP is using an external disk drive, unknown filesystem type (will wager FAT32), so rsync won't work.

Ah...true.  I often forget about other file types.  Yes, rsync is the way to go, but it assumes you have ext3 or ext4 on the target file system.  

As an aside, if you must use tar, why do you want to get your entire disk?  if you get /home and /etc you will have about everything you would need in the event of a problem.  Or...one of / once a month, then pull /etc once a week and /home every day.  

I just get /home and /etc along with my dedicated /documents drive and I can get going from a clean install now in about 2 hours (I just did a clean wipe to install 9.10 64 bit).

Rather than backing up the files in / I simply keep a log of the applications I install, so I can install them all at once on the next pass.

---

### Post by blueridgedog on 2009-11-16
> **Giblet5 said:**
> 
The rsync command doesn't preserve symbolic links, and the command as given above won't even preserve permissions or timestamps. Why even bother.



The "a" option is the archival option and preserves permissions, owner, group and many other features.  Time stamps are included by default, as that is essential in knowing which files are newer.

From the man page:

```
-a, --archive
              This  is equivalent to -rlptgoD. It is a quick way of saying you
              want recursion and want to preserve almost everything  (with  -H
              being  a  notable  omission).   The  only exception to the above
              equivalence is when --files-from is specified, in which case  -r
              is not implied.

              Note that -a does not preserve hardlinks, because finding multi&#8208;
              ply-linked files is expensive.  You must separately specify -H.

```

---

### Post by Giblet5 on 2009-11-16
Just to pile contusion upon confusion, I'll add that the -u option to tar will perform an incremental update of an archive, dramatically decreasing the space utilization and time requirement of a full backup.

Like rsync -urH

So, let's review: rsync can do full backups to a linux filesystem via the -aH option string. It creates mirror copies and can effectively synchronize one local or remote directory to another local or remote directory. There is no compression, so backup storage must match or exceed that of the media being backed up. The rsync command is an optional add-on for many operating systems. Because rsync requires a same-filesystem target, it is not easy to access backup data from operating systems that don't have support for the target filesystem type.

The cpio command is optional on many operating systems and unavailable on some (MVS, VMS, etc), and is more of an archiving filter than a full-featured archival program. It does not support an update operation, so every backup with cpio is a full backup.

The tar command is installed by default on any Unix-like, or BSD-like OS, and is available on every operating system (even AmigaDOS, MVS, VMS, and VMS-spinoffs like Windows NT). Its archives are reasonably compatible, even between operating systems of differing architecture (eg, little v big endian - a major shortcoming of cpio). It can compress its archives using compress, lzha, gzip or bzip2 compression, and it supports updates for incremental backup purposes. Winzip and Winrar can read and update tar's archives whether they are compressed or not. The tar command can write its archives to any filesystem capable of creating files of adequate size, or it can write its archives to tape, CD, DVD, Blu-Ray, remote systems, or if extremely high throughput is needed, directly to block or character special devices.

Did I miss features?

Anything to add?

If so, copy the whole set of descriptions to a code block and make your changes. We'll create a sales brochure for native backup mechanisms!

---

### Post by jhann on 2009-11-17
Right, I appreciate all your help guys - so I'm going to use rsync and will be using the following command:

rsync -av / /toshiba --delete --log-file=/home/james/Desktop/$(date +%Y%m%d)_rsync.log --exclude 'toshiba'

This will sync up everything in / to /toshiba (excluding the toshiba dir?), what does the --delete --log bit do? Does it delete the old log and then write a new on in /home/james/Desktop/rsync.log? 

I'll give it a shot on my lunch in 1 hour, thanks.

oh, will I be able to boot of of this copy?

---

### Post by blueridgedog on 2009-11-17
The --delete means to delete anything in the destination that has also been deleted in the source.  The log file creates a log of the synchronization.  It is not bootable, but that can be fixed by installing grub to the disk in the event that it is required.

With the --delete option, you want to be careful to keep your source and destination clear.  I suggest you run it the first time or two without it.

---

### Post by Giblet5 on 2009-11-17
No, you won't be able to boot off of that copy, even if you install grub, because that command line will not create a complete copy.

To be able to boot off of the copy, /toshiba must be the same filesystem type as / and the command line must be:

```
sudo rsync -aHv / /toshiba --delete --log-file=/home/james/Desktop/$(date +%Y%m%d)_rsync.log --exclude 'toshiba'
```

-H preserves links. About 10% of the files on / are links (see /etc/rc*.d for example).


Also, in order for the backup disk to boot, it will be necessary to modify /toshiba/etc/fstab to correctly identify the / filesystem.

---

