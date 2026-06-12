---
title: "Partition got changed from physical to logical. Need to restore data."
date: 2010-09-11
forum: General Help
---

### Post by nstgc379 on 2010-09-11
The partition isn't corrupt, per se, but some how sometime last week one of my partitions was changed from a physical partition to a logical partition (I just found out now). Now a large chunk of data is missing.

The partition in question is an ext4 partition, which should be very similar to an ext3 partition. Any good intuitive, easy to use programs that could help. So long as it runs on either Windows 7 or Linux and is idiot retardant I don't care what it is. I tried to install extundelete, but for whatever reason the configuration script isn't recognizing the C++ compiler. I have no idea how to use Mondo and gddrescue simply isn't working.

Oh there is one other requirement -- if it is a Linux program, it has to run from a live CD. I don't want to boot into my actual OS until its fixed.

Also, I don't know if this was a good thing to do or not, but I fsck'ed the partition. It didn't return a single error.

There do not appear to be any missing data on the other ext4 partition, however I leave it unmounted unless I need it. Its on the same drive so I fsck'ed it as well. I haven't run check disk yet, but I will later today.

[edit] When I say the output was normal, I mean completely. Its as if I had deleted the file manually. Also, I absolutely did **not** do this intentionally. I have no clue how this happened. I haven't messed with the partitions in months. This certainly has happened within a month, likely within days.

Also, I checked and it seems no other users were effect aside from the administrative account (not root, but the one with root privileges). I can't say for certain, however, since only my archival drive has hash tables for file checking.

As for what I am asking for: software that will enable me to copy the "deleted" files to another partition. I don't care if its a Windows program or a Linux program. I would prefer something with a GUI, but command line is fine as well. Actually, if its a windows program I'd like to avoid command line. I don't know if the DOS emulator in Windows is crap or if its just that I've become too use to the Linux terminal (which is far superior to DOS ever was). I'd even be happy if a program that lists what directories should be there.

[edit2] over 1000 files in tens of folder and subfolder were deleted.

Here is the output of "sudo fdisk -lu"

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ad2f149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   437076758   218538348    7  HPFS/NTFS
/dev/sda2      1413848520  1452918599    19535040   83  Linux
/dev/sda3       437080062  1413847039   488383489    5  Extended
/dev/sda4      1452918600  1953520064   250300732+  83  Linux
/dev/sda5       437080064  1413847039   488383488   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2048 MB, 2048728064 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4001422 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079784

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     4000184     2000061    b  W95 FAT32
ubuntu@ubuntu:~$ 

```

---

### Post by Mark Phelps on 2010-09-11
Not sure what you're asking -- but there is no program that will run in MS Windows and be able to read Ext4-formatted partitions.  So, if that is what you're looking for, you're out of luck.

---

### Post by efflandt on 2010-09-11
In Linux what is the output of **sudo fdisk -l** (small L) for that drive, which partition is it, and what did you do to get into that situation?  It would be easiest to fix if it is at the beginning or end of the wrapping extended partition.

I tried changing a primary partition to a logical partition once with Linux fdisk (by removing it, creating an extended partition, then a logical partition the original location/size), but that did not work, so I changed it back to a primary partition and it still worked fine.

---

### Post by nstgc379 on 2010-09-11
The output is completely normal. There is nothing. I tried -fvv and there was nothing extraordinary at all. It was as if I had moved the files to Trash and then deleted them permanently.

As for how I did it, I have no clue. It certainly wasn't intentional.

Its one of three partitions on that drive. The other two seem to have been untouched.

Also, there have been no non-clean dismounts -- no power outages, no instances in which I turned the power off without issuing the command.

[edit] @efflandt:

```
ubuntu@ubuntu:~$ sudo fsck -l /dev/sda5
fsck from util-linux-ng 2.17.2
Usage: fsck.ext4 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list

```

I'm checking for bad blocks now (sudo fsck -c).

---

### Post by srs5694 on 2010-09-11
You seem to be asking about two different issues, and I'm afraid you're not being very clear about either of them. Specifically....

> **nstgc379 said:**
> The partition isn't corrupt, per se, but some how sometime last week one of my partitions was changed from a physical partition to a logical partition (I just found out now). Now a large chunk of data is missing.

First, there's no such thing as a "physical partition" in the usual partitioning parlance. I suspect you mean "primary partition." A change from primary to logical partition is a bit tricky to pull off even if you're attempting it, and I don't recall ever before hearing of it happening accidentally. Therefore, my suspicion is that you're mistaken about the partition having changed from primary to logical; chances are it was logical all along.

Nonetheless, if you could post the output of "sudo fdisk -lu", that might give us a clue if there's some abnormality. Note that I (and efflandt earlier) are asking for *fdisk* output, not *fsck* output; they're two very different programs!

> As for what I am asking for: software that will enable me to copy the "deleted" files to another partition.

What files were deleted? Were these system files on the main system partition? User data files in /home? User data files elsewhere?

Running fsck, as you report having done, is normally an appropriate  response to filesystem corruption. As you say that it reported no  errors, however, this makes me think that the lost files aren't the  result of filesystem damage, but of an accidental deletion of some sort  -- a mistyped command, stray mouse click, buggy script, etc. In fact, it's conceivable that they aren't gone, but renamed.

AFAIK, the best utility for recovering lost files on a Linux system is [PhotoRec.](http://www.cgsecurity.org/wiki/PhotoRec) (Despite its name, it can recover lots of file types.) It won't normally recover filenames, though; you'll need to sift through the recovered files manually to figure out what you've got. If you've lost system files, and therefore the ability to boot, you'll do better to re-install Ubuntu from scratch (after backing up /home, if it's on the same partition as your main installation).

---

### Post by nstgc379 on 2010-09-11
I Since a a nightmarish scenario a year ago involving logical partitions, I have avoided them like the plague. Not all of my partitions are automatically checked, as a result I have to do that manually. I do so about once a month. I can't remember what partition is called what so I use gparted to look it up. In the several months since making that partition, I have not noticed a cyan boarder around the partition. It kind of stands out. This is new.

As for what was lost, it was user data. the OS works fine. If it didn't boot, I wouldn't have just found out.

The files are not renamed. The partition went from ~70% used to 5%. They are gone...well the headers are gone. Surely the actual important part of the files are still there.

It is extremely unlikely that I would have deleted so many files without noticing it. I don't use the console to delete files because I have had some accidents before. I have never lost tens of folder, and over 1000 files before, however. I would have known if the stuff was deleted by me.

It may have been a malicious script. that is possible.
ubuntu@ubuntu:~$ sudo fdisk -lu
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ad2f149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   437076758   218538348    7  HPFS/NTFS
/dev/sda2      1413848520  1452918599    19535040   83  Linux
/dev/sda3       437080062  1413847039   488383489    5  Extended
/dev/sda4      1452918600  1953520064   250300732+  83  Linux
/dev/sda5       437080064  1413847039   488383488   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2048 MB, 2048728064 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4001422 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079784

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     4000184     2000061    b  W95 FAT32
ubuntu@ubuntu:~$ 

```

[edit] I tried testdisk, but I was not given the "undelete" option like it shows in the manual. Furthermore, I'm not sure, given the quantity of files, that testdisk would be a good solution.

[edit2] PhotoRec may work. Its currently running.

[edit] PhotoRec may work. I'm not sure. Most of what it got were temporary internet files. Nothing meaningful. I don't have the disk space to store the data, unfortunately so I'll have to wait for my new drive to come.

---

### Post by srs5694 on 2010-09-11
TestDisk is used to recover entire partitions that have been deleted, not individual (or even mass groups of) files, so it's no good to you. Best of luck with PhotoRec.

---

### Post by dcstar on 2010-09-11
> **nstgc379 said:**
> The partition isn't corrupt, per se, but some how sometime **last week one of my partitions was changed from a physical partition to a logical partition (I just found out now**). Now a large chunk of data is missing.

The partition in question is an ext4 partition,
........

Really?, are you **100% sure** that you just haven't started using a different Linux partition and you have mistaken that for what you describe?

If a separate /home partition isn't mounted then guess what it looks like.....

---

### Post by srs5694 on 2010-09-12
dcstar makes a good point. Try posting the output of "df -h" after a regular boot of the system. That will show what partitions are mounted where. If one of your three Linux partitions is missing, it could be you've booted the wrong installation or have mounted the wrong partition somewhere.

---

### Post by nstgc379 on 2010-09-12
I'm very certain. I would have noticed that the partition was the wrong size, when I checked gparted. I certainly would have noticed that my setting were different. The background would have been different. One of those partitions, the small one, is root. Had it simply not mounted the partition I would have had nothing. If it had mounted the other, which at one time was my /home partition, I would have been given errors since that partition didn't house the user data for nstgc. /home/nstgc use to have its own partition on a different, now disconnected, drive.

I do know what it looks like when you try to login as a user without a valid home directory. I can't remember the circumstance, but there is a particular one in which I found the solution was to ctrl+alt+F1 into a console and rename the admin's home directory (ie nstgc --> nstgc0). I've done that a couple time (its been several months since the last time I did that by the way).

So in short, if it had mounted a different partition as home, I would have been given errors.

As for booting the wrong installation, thats not possible since I only have one. I typically keep two in case something happens, but I currently don't have such a installation. Given the absurdity of the situation, it seems possible that I accidentally booted a different kernel image, however, even then, when I booted from the live cd the files would still have been there.

Also, only most of my data was deleted, not all of it.

Just as an FYI, I ran check disk on my windows partition, and everything was clean. I also did a rough check of my main archival drive.

I should make a note that I'm the only person using this computer.

This is certainly bizarre. The drive isn't corrupt, I personally couldn't have accidentally deleted the files. Its not suppose to be possible to change a primary partition into a logical partition (but it did happen). Some of my files still remain. If my other user accounts were effected it was minimal. I'm growing more and more certain that I somehow executed a malicious script. That or I was somehow hacked despite being behind a router with an access list.

I also ran NOD32 in Windows, thinking that maybe, somehow, something may have done this from there.

---

