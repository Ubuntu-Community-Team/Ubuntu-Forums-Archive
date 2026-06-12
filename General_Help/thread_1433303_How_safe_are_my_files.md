---
title: "How safe are my files?"
date: 2010-03-18
forum: General Help
---

### Post by warrior_juggalo on 2010-03-18
I recently filled my 1TB external hard drive and have another 600GB's inside my computer, I want to store my files and keep them on that but i would hate to fill it than it crashes, I'm low on cash right now and don't have the money to buy another external....

So my question is if linux crashes i will still be able to access my files from a live cd or something, How safe exactly is Ubuntu, I've been using it for about 1 year and never had a crash or any problem like it....

Is ubuntu safest for this or is there another Linux distribution that you'd recommend.

PS. my hdd in my computer are 2X74GB Raptors and a 500GB WD, Would it be safer once again to install the OS on one of the 74GB and use the 500GB for all my data?

---

### Post by Mr Nemo on 2010-03-18
I've had ubuntu crash on me once (my own fault, it's when I first got the OS), and in my experience its incredibly easy to retrieve files with the live cd, of course assuming something didn't happen that for some reason completely wiped out your whole hdd. Though, I've never had a problem like that with ubuntu.

---

### Post by bowens44 on 2010-03-18
> **warrior_juggalo said:**
> I recently filled my 1TB external hard drive and have another 600GB's inside my computer, I want to store my files and keep them on that but i would hate to fill it than it crashes, I'm low on cash right now and don't have the money to buy another external....

So my question is if linux crashes i will still be able to access my files from a live cd or something, How safe exactly is Ubuntu, I've been using it for about 1 year and never had a crash or any problem like it....

Is ubuntu safest for this or is there another Linux distribution that you'd recommend.

PS. my hdd in my computer are 2X74GB Raptors and a 500GB WD, Would it be safer once again to install the OS on one of the 74GB and use the 500GB for all my data?

no matter what operating system you use,to be safe, you need to back up important data. Hard drives die all the time.....

---

### Post by warrior_juggalo on 2010-03-18
I didn't know weather to make another topic but a quick question....

Is there any reason one would run the Server version over Desktop?

---

### Post by bobcollard on 2010-03-18
I have three external drives.  Two 250GBs that I use to back up and store on my laptop and one 500GB I use on an old eMac.  The advantage of having an external is not just being able to access it by one system, but, by all systems.  Information is just that, no matter where it is stored.  Most externals are FAT32 format and that is readable and writeable on any system.  If it is NTFS it is still pretty open to most systems.  EXT 3 and 4 are pretty much Linux but that's any Linux system.  When you said safe I hope you didn't mean secure, unless you have it encrypted it is not that safe.  Hmn, I got a TB and more here too.:)

---

### Post by srs5694 on 2010-03-18
I doubt if there's much distribution-to-distribution variability in terms of the likelihood of losing data to bugs or system crashes. There might be some subtle user interface issues or bugs in specific versions of programs that would affect this, but certainly when it comes to hardware reliability or susceptibility to damage in a power outage, you should be looking at issues other than the distribution. In particular, there are hardware configurations (such as certain types of RAID) that can improve the reliability of data storage; however, since you don't have the money for more drives right now, these aren't really options for you. What you could do, though, is look into the reliability of your filesystems and your data layout.

In terms of filesystems, Linux supports quite a few natively. Most Ubuntu users seem to use ext3fs or ext4fs, but other options include ReiserFS, XFS, JFS, and Btrfs. I don't know of any serious scientific study of the reliability of each of these OSes in either normal use or in the event of, say, power failures. The prevailing opinion is that ext2fs and ext3fs are quite reliable, though. Certainly they're well supported and there are good tools for dealing with problems. Ext4fs is still pretty new, and I've seen reports of some problems with it, but this is just anecdotal. I've seen some claims that ReiserFS is not quite as reliable on multi-core systems, but I don't know how true this is. XFS and JFS are both known for reliability on their original platforms (Silicon Graphics' IRIX and IBM's AIX and OS/2, respectively); however, the Linux versions are ports and so may not be as reliable. I've personally seen JFS fail (cause system lockups) under some stress tests, but it seems fine in normal use, in my experience. Btrfs is still new enough that I wouldn't trust it with really critical data.

The other issue you can control is system configuration. If you split your installation into multiple filesystems rather than use a single monolithic filesystem, you can isolate disk problems to part of your system. You can also employ different filesystems or filesystem mount options to minimize risks. For instance, if you split /usr off into its own partition, you can mount it read-only most of the time, which reduces the risk of accidentally deleting files from the system. Likewise for /boot -- or better yet, you can leave /boot completely unmounted most of the time, since it's not needed during normal system operations. (If APT updates your kernel or GRUB, though, /boot *must* be mounted!) In the event of a modest disk hardware failure or filesystem corruption, if you lose a single filesystem because of the problem, you won't lose everything.

If you want to reconfigure your system in this way, you should study the issues carefully. It's easy to go badly wrong with this sort of thing by setting up too many partitions of the wrong size. This can quickly become a problem because you can run out of space in one partition. Resizing it then becomes a risk factor itself.

---

