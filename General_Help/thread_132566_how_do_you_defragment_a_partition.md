---
title: "how do you defragment a partition?"
date: 2006-02-18
forum: General Help
---

### Post by HokeyFry on 2006-02-18
the title says it all. so, how do you?

---

### Post by Perfect Storm on 2006-02-18
You don't. Linux partitions (etx2, etx3 reiser etc.) handle it all by itself. They are built up so no defrag is needed. So there's no need to defrag.

---

### Post by kudu on 2006-02-18
I believe Linux compresses and decompresses everytime you shutdown and reboot. Is that right ?

---

### Post by HokeyFry on 2006-02-18
i did not know that. thank you. i wish windows would do that...

---

### Post by K.Mandla on 2006-02-18
[QUOTE=HokeyFry]i did not know that. thank you. i wish windows would do that...[/QUOTE]
That was my reaction too. :) "Now why couldn't Windows handle that?"

---

### Post by 5-HT on 2006-02-18
I'm not sure, but have heard that if the partition is almost full, then it may fragment more.

If that's the case and you really want to get the partition more contiguous, one  obvious way would be to simply move everything on it do a different partition/drive, then simly move it back onto the partition in question (if you have / on a separate parition I would **highly** suggest just leaving it alone, this is more for separate /home paritions or other data partitions).

HTH

---

### Post by LateNighter on 2006-02-18
I have used any number of Linux Distro's, and have never heard of any type of Defrag needed, because thay have been built not to need it, as well as to take care of itself on StartUp.

 I've heard nothing of it Fraggin when rthe disc gets almost full.

 Why should it start fraggin then if it don't when the disk is'nt almost full.

 But I learned along time ago Not to ask questions of try to figure these things OUT, it'll keep ya up nights, Hence my Forum Name.:KS

---

### Post by 5-HT on 2006-02-18
[quote=LateNighter] But I learned along time ago Not to ask questions of try to figure these things OUT, it'll keep ya up nights, Hence my Forum Name.[/quote]
:mrgreen: 
 
I'm by no means knowledgeable on this subject (so someone please correct me if I'm wrong), but am guessing that perhaps if the partition is almost full, then it becomes harder to save files with some extra space allotments for them to grow, resulting in possible fragmentation if they do.

---

### Post by cilynx on 2006-02-18
As has been said many times before, defrag under Linux is a non-issue.  The ext filesystem was designed to prevent the whole problem.  As for compressing / decompressing the entire filesystem on boot / shutdown, I've never heard that before and I highly doubt it as it would make bootup / shutdown take hours.

What Linux does on boot and shutdown that you never see in Windows is sync /  mount / unmount the drive(s).  Mounting is the process of making the content on the drive accessible.  To sync is the process of making sure that all pending changes to data have been carried out on-disc as opposed to just in the buffers / cache.  Unmounting is doing a sync, then removing the access to the drive.  Once unmounted, the drive can be safely powered down.

Sometimes, on boot, you'll see 'fsck'.  Windows' scandisk is a closer analogy to fsck than compressing / decompressing.  'fsck' == "filesystem check".  If you're using ext2 and you shut down without unmounting the drives (pull the plug), then you'll have to do a fsck on boot to make sure that the filesystem is intact.

Ext3 is what's called a "journaling filesystem".  Basically, it sets apart a chunk of drive to keep track of what's going on.  It writes what it's going to do.  It does it.  It writes what it did.  This way, even if the drive is shut down in the middle of an operation, the filesystem can pick up approximately where it left off.  This eleminates the need for a fsck on boot.  Ext3 still recommends a fsck every 30 boots or so just to make sure things are still going alright.

Probably more than you wanted to know...

---

### Post by ximok on 2006-02-19
If you want to help reduce the little fragementation that does happen (to help keep the system form defragging itself all the time)

make a seperate partition for your /home/ directory and a seperate partition for /tmp/  This will reduce the time the system spends making the drive contigous, plus, you never have to worry about your /usr/bin/ folder having files seperated by user files.

This guide is a safe one to follow to see what directories are pretty safe give their own partitions.
[http://www.tldp.org/HOWTO/Partition/fdisk_partitioning.html#submitted](http://www.tldp.org/HOWTO/Partition/fdisk_partitioning.html#submitted)

Just ignore the partion sizes because some of them are not realistic.

I would dedicate at least 4 gigs to /usr/ at least double the amount of ram you have for your swap space, at least 3 gigs for /tmp/, 15 - 50 megs for /boot/, a gig or 2 for / and everything else for /home/

---

### Post by Fred Doolie on 2006-02-20
You DON'T NEED TO DEFRAG???? [Sneers at his Winblows partition for the 80th time today]

---

### Post by LateNighter on 2006-02-20
[QUOTE=Fred Doolie]You DON'T NEED TO DEFRAG???? [Sneers at his Winblows partition for the 80th time today][/QUOTE]

 Agreed, When will they ever learn???:-({|= 

 I would'nt even MESS with having a Windoze Partition at all if I could get my Wife to Change over.
 But I've got to have it too be able to help her on some of the things She does.:mad: 

 But until then I'll never engage it until SHE requires me to.

 She's afraid if I use Linux to do some of her stuff it won't get done right for her too use.
 I tried to tell her different BUT She WON'T Listen.

 ANYWAY No need to defrag Period...
 Linux lets Windoze take care of that part, And I think it does Pretty Well on it's own.
 It doesn't need any HELP....[-(

---

