---
title: "Need to Move/Combine Partitions"
date: 2006-02-17
forum: General Help
---

### Post by Revert on 2006-02-17
Somehow my disk ended up really messy.  Right now it's something like:

Swap
Root
20 gigs of free space
Home
Extended-3 sub partitions

I need to combine/move things around so I can use that free space and put most of my data into one or two partitions in the Extended section.  

What would be the easiest way to do this?  I have to unmount home, so would I need to use some form of Live cd?

---

### Post by aysiu on 2006-02-18
*Easiest* way? Back up everything and do a fresh reinstall, deleting all unnecessary partitions.

It's generally a good idea to back up your work, anyway. Do it however you can--web space, floppy disks, CDs, DVDs, external hard drives, iPods, zip drives, whatever.

Then get a good partitioning program like DiskDrake (on PCLinuxOS) or QTParted (on Knoppix) or GParted (which can be downloaded and used with the Ubuntu live CD) and repartition as you see fit.

Finally, pop in the Ubuntu installer CD and install it on the appropriate partitions.

---

### Post by Revert on 2006-02-18
With 90+ gigs of stuff to save, I don't know how I'd backup that much. 

I might have enough spare hard drives laying around.....

I'll check it out, thanks.

---

### Post by cotcot on 2006-02-18
Supposing you want to keep the /home you could do it by making a new partition on the 20 GB free space, transferring data from the ext partition, resizing the extended (reduce), resize the new partition, eventually move it and repeating all this untill you have what you want. However these are quite substantial operation with risk of errors that cannot be recovered. So this way may not be the preferred way. The major problem is - as previous post says - the lack of back up strategy. Solving this problem first will make the solution for the first problem a lot easier.

I use a 200 GB USB HDD to backup everything.

---

### Post by aysiu on 2006-02-18
[QUOTE=Revert]With 90+ gigs of stuff to save, I don't know how I'd backup that much. 

I might have enough spare hard drives laying around.....

I'll check it out, thanks.[/QUOTE] I have a 160 GB hard drive I purchased about a year ago. It wasn't cheap, but it was a worthy investment. Just think about it this way: if it's 90 GB of stuff you want to save, it's worth backing up (even if you weren't reinstalling--just to know you couldn't lose it to some freak accident).

I know this is going to sound crazy, but that's "only" about 100 or so burnt CDs.

---

### Post by Revert on 2006-02-18
I can't partition the 20gigs at all because of the whole "4 Primary Partitions" and such.

A lot of this stuff would be a pain to burn on cds because the files are over 700mbs (plus a hundred's a lot for me :???: ).  I think I'm just going to bite the bullet and do some hard drive switching (slave some stuff, transfer, scrounge up another and repeat).

The hard drive it's currently on is a 160 gigger, and my plans are to put it in a fileserver, so once this all works out I'll finally have a backup plan.

Thanks for the help.  I'll probably get started on this this weekend (if I can find time). :)

---

### Post by DaveRowell on 2006-02-18
Revert, I can't stress how correct the post advising a backup is!  Until you have had a harddrive die in the space of a few seconds you just can't appreciate how much you need a backup.  My 8 month old drive just started going clank, clank, clank, clank, clank, clank, clank ... and there went all my data.   As luck would have it I **only** lost 6 months of my life - cruise pictures and some new genealogy information that I can't find again :cry: 

I'll bet a cookie that most of the stuff you have isn't important to you.  Much of it is easily replaced - if you remember where you got it.  Probably a lot of it is just plain garbage and you've been putting off a good housekeeping.  Clean house, bookmark your important sources and back-up the good stuff in any way you can.

Whether you do a fresh install or not you'll be able to sleep better :-?

---

### Post by Revert on 2006-02-18
Actually, most of the stuff's data that's important to me.  I've been shuffling it around on the same harddrive through multiple versions of Windows, my transfer to Linux, and a few Linux distros.  It'd probably be a good idea to do a fresh install for once...

---

