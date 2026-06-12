---
title: "Extra free space is now occupied by something else after partition change"
date: 2006-06-12
forum: General Help
---

### Post by sheilnaik on 2006-06-12
Here's the story:

1. I had a FAT32 partition (40GB) that I wanted to delete and merge with my ext3 Ubuntu partition.
2. I used the Live CD and GParted and deleted the FAT32 partition.  I also deleted the swap partition that I had.  I resized the old ext3 Ubuntu partition to a larger size (50GB) and created a new 1GB swap partition.
3. Before applying changes, GParted said I would have 40GB of free space on my ext3 partition.
**4. I applied the changes and rebooted.  Now, I still have the same amount of free space I had before the partition changes.  The ext3 Ubuntu partition shows that it is bigger, but the 40GB I added is now "Used space".**

My question is, where did all the free space go?  I did a  cd /; sudo du -h --max-depth=1 and I got this:

```

sheil@sheil-laptop:~$ cd /; sudo du -h --max-depth=1
Password:
48K     ./lost+found
440M    ./var
15G     ./media
14M     ./etc
4.4M    ./bin
9.4M    ./boot
120K    ./dev
5.0G    ./home
4.0K    ./initrd
111M    ./lib
4.0K    ./mnt
120M    ./opt
498M    ./proc
3.5M    ./root
11M     ./sbin
4.0K    ./srv
0       ./sys
104K    ./tmp
2.1G    ./usr
23G     .

```

The /media directory is large because it has my other NTFS Windows XP Partition on it, so ignore that.  Two things have me confused though:

1. There are 23G of used stuff in the root directory of the file system?  Nautilus did not show this when I viewed the file system as root (via the gksudo nautilus command).
2. The du still did not account for the 40GB of space that I added from the FAT32 partition.

I have attached a screenshot of my GParted window so you can get a better understand of how my system is set up.  Any and all comments/advice would be useful.  Thanks!

**EDIT:**  Just to clarify, my Trash (for all users, including root) is empty.  Also, I had some stuff (over 30GB worth) on the FAT32 partition before I deleted it.  However, I never deleted the data and sent it to my Trash...I just deleted the partition using GParted on the Live CD.

---

### Post by user1397 on 2006-06-12
have you tried erasing the ntfs partition again? (just erase it and apply changes, and then we'll go from there)

---

### Post by sheilnaik on 2006-06-13
I can't erase the NTFS partition.  That has Windows XP on it, and I'm not about to go ahead and delete Windows XP.  There's no way that partition could be related to this problem (at least, I'm pretty sure its not).  I never touched that partition at all when making my changes with GParted.

---

### Post by mumushi on 2006-06-13
Is your hdd 80GB in size?

---

### Post by sheilnaik on 2006-06-13
[QUOTE=mumushi]Is your hdd 80GB in size?[/QUOTE]

Yes it is.

---

### Post by sheilnaik on 2006-06-13
Bumping this topic, only because I really need to get this problem solved ASAP.

---

### Post by sheilnaik on 2006-06-13
Well it seems that someone has answered the question over at [http://ubuntuforums.org/showthread.php?t=171886&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=171886&highlight=resize2fs).  I'm going to try this method myself as soon as I finish downloading the Live CD here at work.  I'll reply back with an answer as to whether it worked or not.

---

### Post by bigmell on 2006-06-13
By default when an ext3 filesystem is formated 5% is reserved for root. This is done to keep fragmentation low as well as allow root to perform file maintenance stuff. You can change the amount of reserved space by using the tune2fs command. 

This caused me problems for a while on a big drive when I converted it from fat32 over to ext3

---

