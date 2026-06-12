---
title: "Partition Scheme for single drive - Fundamentals"
date: 2011-04-29
forum: General Help
---

### Post by noriek on 2011-04-29
Hello all.

I am, for the first time, considering a reasoned partition scheme for a linux distribution as it seems like a simple way to maximise performance.

I want the scheme to consider 2 factors: First, linux's directory structure, and second, the part of the disk (tracks, cylinders etc) where each partition is placed.

On the second point, can someone clarify which part of the disk is the fastest: the inner or outermost tracks? I've read a lot on conflicting information on the matter. Obviously the outer tracks have a higher linear velocity but of course they are 'bigger' so I'm not sure which factor is more important. On the same lines, if I create a partition at sector 1 on a disk, is this the inner or out track?

With regards to directory structure, which directories deserve their own partition on a standard home computer i.e. not running a mail server so /var won't see that much action. In this case might I just as well leave it on the 'main' partition? How large a partition should I leave for /boot and /root on a modern distribution given kernels and bootloaders are much bigger than they once were?

Any other factors I should consider in theory and or in practice?

Appreciate any tips.

p.s. drive is a Samsung Spinpoint F3 1TB

Thanks

---

### Post by mikewhatever on 2011-04-29
I think that for a home computer, all you need is the root partition. Some like creating a separate home for easier reinstallations, but technically, that's unnecessary. As for the location, I rather doubt you will notice any substantial difference in speed, depending on where you create the partitions.

---

### Post by noriek on 2011-04-29
Hi Mike....,

I don't know that effect will be minimal or unnoticeable: it's seems to be common practise in RAID 0 setups to place the system and program files on the fastest part of the disk. Also, evidence for partitioning improving effective seek times seems at least worthwhile, in my opinion, especially as harddisks are obviously the bottleneck in most systems, apart from those with the fastest SSDs. Additionally, this Samsung drive has been proven to be particularly quick in the budget range, faster than previous models of Seagate Barracuda, so I'd like to optimise it.

Regarding home partitions, I usually store personal files on something like /storage so /home/* is relatively irrelevant in my case.

What about /var and /temp whose size often fluctuates?

---

### Post by Lateralis on 2011-04-29
For a home computer you are unlikely to ever notice a performance increase through the judicious choice of which partition goes on the inside or outside of the disc.  For servers or for setups where speed is of utter, paramount importance then this is something to be considered.  So on this point I wouldn't worry.  As a home user you will notice no speed difference.  

As for different partitioning schemes, they are mostly useful for when you have to reinstall the OS.  I have a separate /home partition, as /home is where user settings and personalisations get stored.  You could also have separate /usr/local and /opt partitions, as these are typically where user installed programs get put.  You can also have a separate /boot partition, but I'm not sure how useful that really is.  If you did want a separate /boot partition, a few hundred megabytes will be more than enough.  Mine is 200 MB and is currently 48% full.  My /home is 40 GB and 51% full.  

But some of this is fairly unnecessary though.  I've just learned how to restore your system to a previous state using the following:

```

sudo dpkg --get-selections > /path/to/savefile
sudo dpkg --set-selections < /path/to/savefile && sudo apt-get dselect-upgrade

```

The first creates a file listing all of the currently installed packages.  The second reads in this file and installs them.  So long as you have a separate /home partition then all of your personalisations for all of these installed programs will remain.  

As for /var and /temp they don't need to be separate partitions.  For servers, having a separate /var is good, but again, as a home user, don't bother.

---

