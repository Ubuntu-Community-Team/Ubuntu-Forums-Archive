---
title: "Confusing low disk space warning"
date: 2012-08-30
forum: General Help
---

### Post by Heathicus on 2012-08-30
I've been getting this low disk space warning occasionally for a while that I can't figure out.  

"The volume "Filesystem root" has only xxx MB disk space remaining."

It will tell me I only have a couple hundred MB of space left, but all investigation on my part shows that I have over a GB free on the partition/disk with the lowest amount of free space.  So I've just been ignoring it as the number seems to fluctuate.  Sometimes I'll move some files around and that seems to satisfy it for a while, but then the warnings will return.  Sometimes I get the warning right after a reboot, sometimes it just pops up in the middle of whatever I'm doing.  It just really has me confused.

For example, the last time I got the warning today, it said I had 612.4 MB free space remaining (usually this number is down around 200 or 300 MB, although sometimes as high as 1.5GB).  I clicked the "Examine" button and it scanned my file system.  

I have 2 hard drives.  A 600GB drive divided into 3 partitions; 1) 25GB Win7, 2) 25GB Ubuntu 10.04, 3) the rest "Data."  Then I have a 2TB hard drive that is one partition called "Data2."

The file system examination shows that I have a "Total filesystem capacity of 2.3TB (used: 1.9 TB available: 493.8GB).  I'm not a mathemagician, but I'm pretty sure that 493.8GB is more than than 612.4 MB.  

So, I'll have to look at each disk individually.  The only way I know how to do that is with something like GParted.  GParted shows that the Win7 partition (which I never boot to and don't even have mounted in Ubuntu) has 1.81 GB free.  The Ubuntu partition has 1.63 GB free.  And the "Data" partition has 36.17 GB free.  The "Data2" disk has 455.94 GB" free.  All numbers much larger than 612.4 MB.  

So, where is Ubuntu getting that I only have 612.4 MB free?  Where is that number coming from?  What am I not understanding about the Ubuntu file system?

---

### Post by oldfred on 2012-08-30
Ubuntu hides 5% so you do not crash system when you run out. That may be part of it.

What is taking all the room?

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

This should show usage.
df -H

---

### Post by lukeiamyourfather on 2012-08-30
Why only 25 GB for each operating system? That's barely enough for a fully featured modern operating system (with updates, third party software, paging/swap file, etc.) as you're discovering. I could see such conservative partition sizes if the disk was only 80 GB but you have literally thousands of GB to work with.

Ubuntu "hides" 5% because running with that little of free space is bad, aside from the possible hard crash. It increases fragmentation which reduces performance. For the best performance partitions should not be filled more than 85% of their capacity. As a stopgap to free up some space you could move some of the files with rsync (rsync -a --progress /source /destination) to another partition and then use a symbolic link to point to them.

---

### Post by dcstar on 2012-08-31
> **Heathicus said:**
> 
........
**The Ubuntu partition has 1.63 GB free.**

So, where is Ubuntu getting that I only have 612.4 MB free?  Where is that number coming from?  What am I not understanding about the Ubuntu file system?

That is the **root partition** and can easily be filled up with temp files, all else is totally irrelevant.

Clear out your downloaded packages cache or expand the root partition - do a search for detailed instructions.

---

