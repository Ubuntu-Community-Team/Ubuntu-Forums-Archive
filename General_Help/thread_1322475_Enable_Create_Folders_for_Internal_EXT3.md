---
title: "Enable Create Folders for Internal EXT3?"
date: 2009-11-11
forum: General Help
---

### Post by oldefoxx on 2009-11-11
I'm back to 9.04 for the present.  No point to keep railing against issues I found with 9.10, as it will likely take time to see those addressed and resolved.  Besides, I find 9.04 to be a very good OS to deal with.

But, something I would like to get resolved if I can.  I've a fair amount of hard drive space, but have divided it all up into a number of partitions so that I can have different OSes installed and be able to elect which one to boot up next.  I can also surrender a partition to a different OS and not give up much in the effort.  That way I can move ahead when the time seems appropriate.

But, to maximize what I have, I have a special NTFS and a special EXT3 partition with no OS, just space to store data and downloads that might be used with each of the related OSes.  And what I find, is that though I can get access to the NTFS partition well enough from Ubuntu and Windows both, I cannot access the extra EXT3 partitions from within Ubuntu well enough to mount or dismount them at the GUI level, and the options to Create Folder and Create Document on those mounted partition are both marked in light gray.  And under Properties for the EXT3 partition, I see root in contol.

Now I've done lots of searches for some answers, and while some of the methods suggested (chown and chmod) seem to work for others, I've had no success myself.  There is no kickback from entering the commands, but there is no change either.

So I was wondering if anyone reading this has wanted to do the same thing and worked out a solution.  I suppose I could revert down to the console terminal mode and use sudo to do a mkdir each time I want to add a folder, but I am interested in seeing if I can get to a point where I don't have to do it that way.

I also know that if I reformat the partition, presumably I get the means of creating folders as well, but if I try it this way, then the only install of Ubuntu that will have access will be the last one to reformat that partition.  I want to assume that the data to be conserved is already on that partition, and a reformat would just wipe it out.

I'm going to ask that you not just give me an answer that should work, but that you actually test it yourself before you submit it, because the same answer keeps coming up,  but after trying it many ways over a period of time, I never once got it to change the partiton permissions or ungrey the Create Folder and Create Document options when the partition is right-clicked.

---

### Post by oldefoxx on 2009-11-11
I think I got it.  At least I can create folders now.  In /etc/fstab, I went to the ext3 entry for the partition in question, and changed the options from some of the other settings suggested elsewhere to just this:  defaults,rw.  A reboot, and so far everything seems fine.

---

### Post by coffeecat on 2009-11-11
Hi.

Yes, it seems that you've sussed out that the problems you are getting with the ext3 partition is that when you mount it from Places, it gets mounted owned by root. Which is a nuisance. Personally, I think this is one of the papercuts that the Ubuntu dev team need to be looking at. The reason for this is, of course, Unix/Linux permissions....

Anyway.... :wink:

Basically, there seem to be three solutions.

* Change the ownership of the mountpoint from yourself to root. The mountpoint is (usually) in /media and personally I don't like changing the ownership of system folders - so I'll skip that.

* Use an /etc/fstab line that mounts the ext3 partition and allows an ordinary user to read/write. Except that I've never found the options to make this work - I'm sure they exist.

But here's my suggestion. It's a bit inelegant, but it works and it doesn't involve a line in fstab. You can mount from Places and still read/write. You have to create a single folder in the root of the partition for all your stuff.

1 Go to Places and mount the ext3 partition. When the Nautilus window opens, click on the little notebook-like icon by the breadcrumb trail to get the path to the mountpoint. Let's assume this is "/media/mountpoint". Change the instructions below as necessary.

2 Now open a terminal to create the special folder:

```
sudo mkdir /media/mountpoint/mystuff
```Change "mystuff" to whatever you want.

3 Now change the ownership of mystuff:

```
sudo chown yourusername: /media/mountpoint/mystuff
```Obviously, substitute your account name for yourusername and don't forget the trailing colon. And that's it. Now, whenever you mount that partition from Places, you'll see two folders: lost+found (leave it alone) and mystuff. Simply double-click on mystuff and you'll be able to create folders, save files, and do whatever you want in there.

---

### Post by oldefoxx on 2010-02-12
Nice to see others working things out as well.  I even read of a way to have the root able to log into the GUI in some releases, but there is a specific block against doing this in others.  Seems a shame in a way, as it tends to force root or super user to rely strickly on the Terminal mode and command line to get any work done, and that is not only time consuming, but fragile, since you have to know exactly what commands to use and how to use them just to get a few necessary things done.  That's not where most people live, and yet we have to maintain our own installs, so it goes against what we want to see in place, and what the drivers behind Ubuntu want to permit us to do.

---

