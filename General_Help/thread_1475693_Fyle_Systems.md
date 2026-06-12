---
title: "Fyle Systems"
date: 2010-05-07
forum: General Help
---

### Post by GNUinU on 2010-05-07
Good morning everyone!
I've been using NTFS for all my internal and external hard drives for the most part of my life, but I'm swapping to Ubuntu these days and asked a friend about the FS to use in my data drives.

I'm using EXT4 for the / and /home partitions, but I don't know what to use in my data one (different physical drive) and all my external ones. I was told to use XFS, but after "googleing" a bit stuff like "xfs vs ntfs" I found some information saying that XFS was way too dangerous in data loss terms.

These different links say that in case of a power failure (not very likely to happen but there's a reasonable possiblity) XFS could mean a corruption of the whole HD or some important data loss.

I tried to look for some information talking about this exactly, but didn't find anything concrete. I could say all FS can result in data loss after a power failure, but I just wanted to know if XFS is a weaker FS in this aspect.

My use of these drives is simple. Data backup. No ghost images or big tar files. I just mean a large amount of files. A lot of small ones (from 100KB (docs and xls) to 5MB (mp3)), but a lot of them being single files between 10 and 30GB (mkv).


Thank you all guys.

---

### Post by mikewhatever on 2010-05-07
You could keep using ntfs, as Ubuntu supports that file system out of the box. It is also advantageous, if you need to access the files from a Windows system. On the other hand, you could use ext3 or ext4.

---

### Post by ajgreeny on 2010-05-07
Keep all the internal disks as ext3 or ext4 and the externals as ntfs.

This will give you the ability to use the externals on any windows machines if needed at any time, but will keep the internal disks, which let's face it will not be used by windows if you are not dual booting, with a better linux type file system.  The one disadvantage of this is that file permissions are not kept exactly the same when on ntfs, so backups etc etc if that is what the externals are used for, could throw up occasional errors, depending on how you backup the files.

---

### Post by GNUinU on 2010-05-07
Thanks for the tips guys, maybe I should add more info: :)

I have a dual boot system, but I do all my tasks in Linux now. I've got three hard drives, 2x36GB Raptors and a 1TB Seagate drive.
Windows 7 in HD1 (36GB) and Ubuntu 10.04 in the second 36GB disk. I then have the 1TB drive partitioned this way: 50GB NTFS partition and the rest in XFS right now.

In case I need to share something with Windows, I'll copy it from Linux (/home or XFS partition) to the NTFS partition so I can access it from Billy's OS.

So... don't worry about Windows compatibility as I don't care about it, I won't be using my external drives with it.

And about the backup of the files. I probably used the wrong word. I meant "saving" the files, for example: I get a bluray and make a backup with my PC in MKV format. I put it in my internal drive to save it and copy it to an external drive just in case my internal drive data is ever lost.


I hope I explained it better this time.

Any thoughts?


Thanks!!

---

### Post by mb_webguy on 2010-05-07
Any linux-only partitions should be a something like ext4 (which is Ubuntu's default) or XFS (or some other filesystem that respects linux-style file permissions, while Windows-only partitions and partitions which are to be shared between Windows and Linux should be ntfs.

For example, I have a dual-boot system with Ubuntu and Win7, with two 150GB physical hard drives.  On the first hard drive I have a 25GB ntfs partition for Win7, a 10GB ext3 parition for Ubuntu's root ("/") directory, a 2GB swap partition,and another ext3 partition taking up the remaining 100+GB of that drive mounted as Ubuntu's home ("/home") directory.  The second hard drive is formatted as a single ntfs partition.  None of the ext3 partitions are mounted in Windows, and of the ntfs partitions, only the large one on the second drive is mounted in Ubuntu (so neither OS can see the other).  I have my Documents, Downloads, Music, Pictures, and Videos folders for both OSes located on the large ntfs partition -- in Windows, I changed the locations of those folders in my user folder, and in Ubuntu I mounted the partition under /mnt/stuff and created symlinks in my user directory to those folders (e.g. /home/matt/Documents points to /mnt/stuff/Documents).

So since Ubuntu is my primary OS, I have a large user directory to work with, and all of my data is transparently shared between Ubuntu and Windows.  If I want to open a particular document or play a particular song, all I have to do is look in my Documents or Music folder, whichever OS I happen to be using at the time.

And yes, as for external drives, they should be ntfs if not FAT32, for best compatibility between different computers.

---

### Post by GNUinU on 2010-05-07
I know the best compatiblity would mean NTFS for external drives and also for internal (if shared with Windows).

But these external hard drives are for my use only, and their only objective is to keep data I don't wanna lose, (with data I mean .doc, .xls, .mp3, .mkv, and so on). They'll be only used in Linux, as that's the OS I'm using to backup all these different files.

My interal drive has been partitioned to have a NTFS partition and a XFS one. One for Windows and the other one for Ubuntu. Theorically, the NTFS one will always be empty, as I don't start up Windows anymore. I have it just in case. The only time I'll use the NTFS partition is if I wanna use a concrete file under Windows, which I don't see likely to happen.

**So this is my question:**
Is XFS unsecure? Is EXT4 more secure? I just want to have a FS which I don't have to worry about. I just don't see the point of having my external drives in NTFS when I'll only be using them in Ubuntu.


Thanks guys!

---

### Post by Animal X on 2010-05-07
> **GNUinU said:**
> I know the best compatiblity would mean NTFS for external drives and also for internal (if shared with Windows).

But these external hard drives are for my use only, and their only objective is to keep data I don't wanna lose, (with data I mean .doc, .xls, .mp3, .mkv, and so on). They'll be only used in Linux, as that's the OS I'm using to backup all these different files.

My interal drive has been partitioned to have a NTFS partition and a XFS one. One for Windows and the other one for Ubuntu. Theorically, the NTFS one will always be empty, as I don't start up Windows anymore. I have it just in case. The only time I'll use the NTFS partition is if I wanna use a concrete file under Windows, which I don't see likely to happen.

**So this is my question:**
Is XFS unsecure? Is EXT4 more secure? I just want to have a FS which I don't have to worry about. I just don't see the point of having my external drives in NTFS when I'll only be using them in Ubuntu.


Thanks guys!
i hear ntfs is more reliable, but i couldnt quote any stats(maybe better recovery options?)

---

### Post by srs5694 on 2010-05-07
> **mb_webguy said:**
> Any linux-only partitions should be a something like ext4 (which is Ubuntu's default) or XFS (or some other filesystem that respects linux-style file permissions, while Windows-only partitions and partitions which are to be shared between Windows and Linux should be ntfs.

Absolutely right. Linux lacks good NTFS checking/repair tools, so using NTFS for Linux-only storage is just setting yourself up for trouble -- as soon as there's a power outage or system crash, the disk will require a boot into Windows to be fixed, and if you seldom or never boot Windows, that'll be a nuisance. If you ever remove Windows from the computer, it could become worse than a nuisance. There's also the question of performance. I don't have benchmark data handy, but I'd be shocked if NTFS was as fast a performer as most Linux-native filesystems under Linux, particularly since the NTFS-3g driver used by Ubuntu is a user-space driver, meaning that it's working under some technical performance handicaps. NTFS also lacks filesystem features used by Linux, such as Unix-style ownership and permissions. This might or might not be important for specific purposes right now, but why handicap yourself?

As to the question of XFS's reliability, if you want an evaluation of the claim that XFS is unreliable after a power failure, please post links to the sources of these claims. I don't recall ever hearing them before. FWIW, I use XFS for storing the videos on my MythTV box and it's never given me a problem, in about 3 or 3.5 years of service. XFS performs better with big files than does ext3fs, although ext4fs is probably in the same ballpark as XFS on this score. I still see occasional reports of ext4fs problems, but they're getting rare. In my experience, the biggest drawback of XFS for storage of big media files is that the filesystem cannot be easily shrunk, so if you need to reallocate disk space you'll have fewer options with XFS. (You can increase the size of an XFS partition, though; you just can't shrink it.)

---

### Post by GNUinU on 2010-05-07
> **srs5694 said:**
> 
As to the question of XFS's reliability, if you want an evaluation of the claim that XFS is unreliable after a power failure, please post links to the sources of these claims. I don't recall ever hearing them before. FWIW, I use XFS for storing the videos on my MythTV box and it's never given me a problem, in about 3 or 3.5 years of service. XFS performs better with big files than does ext3fs, although ext4fs is probably in the same ballpark as XFS on this score. I still see occasional reports of ext4fs problems, but they're getting rare. In my experience, the biggest drawback of XFS for storage of big media files is that the filesystem cannot be easily shrunk, so if you need to reallocate disk space you'll have fewer options with XFS. (You can increase the size of an XFS partition, though; you just can't shrink it.)

That's exactly what I needed to read. I'm formatting all my external drives to XFS and putting data back into them again. Working perfect so far. I just needed someone to tell me that was not a mistake.
(They're only gonna be accessible by me through Linux, so no need for Windows compatibility).

The link that put me in warning state was [this]("http://ubuntuforums.org/showthread.php?t=255441"). (same forums aparently... haha)

> Incidentally, do you have a UPS? Afaik the use of XFS without one is very dangerous ... it's hugely RAM-intensive, so it reacts rather badly to sudden power loss!

I know I know... 2006... but I got scared anyway. LOL

That post made me search the web and found some others, but none of them from 2009 or 2010. I don't know.

I decided to keep formatting my drives when I read the [Wikipedia XFS entry]("http://en.wikipedia.org/wiki/XFS"), as I assumed it's always updated.

> 
Specifications
[...]
Journaling

Journaling is an approach to guaranteeing file system consistency even in presence of power failures or system crashes.

[...]

In the event of a system crash, operations immediately prior to the crash can be redone using data in the journal, which allows XFS to retain file system consistency. Recovery is performed automatically at file system mount time, and the recovery speed is independent of the size of the file system.


Thanks!

---

### Post by srs5694 on 2010-05-07
That's a rather vague and nth-hand post. I don't want to make any strong claims about XFS's reliability in the face of power failures, since I've neither done any studies of this myself nor have I read anything I'd consider reliable on the topic. The fact that I *haven't* seen memorable or large numbers of posts about problems, though, suggests that it's at least tolerably reliable. Of course, no filesystem is perfect, and losing power *could* cause problems for *any* filesystem.

As to journaling, it helps speed up data recovery, but it doesn't really help make the filesystem more robust against problems. (A journal is just a record of what areas of the disk have been modified recently. Without it, the entire disk must be checked for consistency after a power failure. With a journal, the disk check can concentrate only on the in-use areas, which speeds things up.) Ext3fs, ext4fs, ReiserFS, JFS, XFS, and Btrfs all include journals. Of current Linux native filesystems, only ext2fs lacks a journal.

---

### Post by GNUinU on 2010-05-07
Yeah, I know what you mean. My biggest worry was this thing about the XFS being much more insecure than any other fs, which I couldn't believe. That's the reason why I needed to create this thread and solve this doubt out. =)

So I'll keep working on this. I've got so many TB of data because of my job, and the process is slow: I first formatted my internal drive to XFS (1TB) and what I'm doing now is plugging an external drive and transfer everything to the internal drive, format it to XFS and transfer it back in again. Crazy!

---

