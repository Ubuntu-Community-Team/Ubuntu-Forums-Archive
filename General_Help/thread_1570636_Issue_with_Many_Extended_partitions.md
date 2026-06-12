---
title: "Issue with Many Extended partitions"
date: 2010-09-08
forum: General Help
---

### Post by beastrace91 on 2010-09-08
Howdy All,

So I have a 640gig hard drive that is currently formatted as one extend partition. This is extended partition is then broken up as follows:

4 gig - Swap
300 gig - EXT4 (Storage)
60 gig - EXT4 (Ubuntu 10.04 Root)
20 gig - EXT4 (Ubuntu 10.10 Root)
20 gig - EXT4 (PCLinuxOS Root)
200gig - Open/Un Partitioned

When I went to install Fedora 13 to the next 20 gigs, the partitioner threw an error telling me it needed to wipe out my drive in order to proceed, I told it to cancel instead. I now no longer can see my partition layout in GParted (On Ubuntu 10.04 or a Live Disc) instead it just shows the whole drive as un partitioned space:

[IMG]http://i53.tinypic.com/2ilhnyu.png[/IMG]

What did I do and can it be un done with out wiping the hard drive? I'd really like to install Fedora and another distro or 2 (don't ask why, I'd just like to do it).

Halp!
~Jeff Hoogland

---

### Post by ks07 on 2010-09-08
You could try using TestDisk from the live cd to recreate the partition table on the disk - it has worked for me before, but it may take some time to scan your entire drive. It's available in the repos. Check the website [here]("http://www.cgsecurity.org/wiki/TestDisk") for some guidance on how to use it.

---

### Post by beastrace91 on 2010-09-08
> **ks07 said:**
> You could try using TestDisk from the live cd to recreate the partition table on the disk - it has worked for me before, but it may take some time to scan your entire drive. It's available in the repos. Check the website [here]("http://www.cgsecurity.org/wiki/TestDisk") for some guidance on how to use it.

Thanks! I'll give that a try.

Off question - there is no limit to the number of partitions I can have on an extended is there?

~Jeff

---

### Post by ronparent on 2010-09-08
As a practical matter, no.

---

### Post by ks07 on 2010-09-08
> **beastrace91 said:**
> Thanks! I'll give that a try.

Off question - there is no limit to the number of partitions I can have on an extended is there?

~Jeff
I believe there is a limit - but it's very high, about 255 logical partitions iirc.  Can't think of anywhere that might be a problem! :p

---

### Post by beastrace91 on 2010-09-09
So testdisc finds the partitions, but they are all marked with "D" for deleted. How to I recover them? It says use the left right arrow keys to change they type, however I cannot set them to extended as they should be...

[IMG]http://i51.tinypic.com/20hn42p.png[/IMG]

~Jeff

---

### Post by ks07 on 2010-09-09
Can you change them to anything at all? Or does it always stay as "D"? Remember that the partitions should not be Extended - rather they should be Logical partitions inside a larger extended partition. Afaik, testdisk does not show the extended partition until you continue to the next screen. 

First thing I'd try is see if you can actually change the partitions from deleted to anything at all (or preferably to what they were previously!). 

After that, press enter, and you should be presented with an overview of the recovery process so far. If you managed to change the partition types, and everything looks good on this page, write the changes to disk. However, if that didn't work, and they all still show as "D" or deleted, you could try running the Deeper Scan option. This may uncover something that was preventing you from making changes.

If neither option works, and you still can't get the program to change the partition table, I'm lost. Possibly a bug in the program - try enabling the logging option when you start the program and have a look through that after running.

Ofc, there are other options to recover lost partitions: [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

---

### Post by srs5694 on 2010-09-09
If you can get TestDisk to recover your partitions, then that's certainly a viable approach; however, I suspect the partitions are still defined, but there's a small error in the partition table that's giving GParted fits. Details are on [this Web site of mine.](http://nessus.rodsbooks.com/missing-parts/index.html) If you're comfortable with command-line tools and arithmetic, you can fix it with sfdisk, as described on that page.

Concerning the limit on logical partitions: In terms of the on-disk data structures, the limit boils down to being just under half the number of sectors on the disk -- but if you went to this limit, every partition would be a dinky 1-sector partition. There may be a lower limit in the Linux kernel, but if there is, I don't know what it is.

---

