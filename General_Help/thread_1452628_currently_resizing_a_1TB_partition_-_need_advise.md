---
title: "currently resizing a 1TB partition - need advise"
date: 2010-04-12
forum: General Help
---

### Post by eanema on 2010-04-12
Hi,

I have a 1 TB drive that is formatted as a single fat32 partition. This data is not critical - IE is multimedia, but I would *really* like to avoid losing data. I wanted to change this partition to ext4 because of permission problems as well as the large file size limit of fat32.

The drive has 780 GB used and about 150 GB free. My plan was to resize the partition and create a new ext4 partition, then move 150 GB over to the new partition. Once done, then I would resize the FAT2 partition again and repeat.

I didn't read much on the topic before hand because I wasn't expecting a problem. Now 6 hours later, Gparted is still resizing my partition. I am afraid to cancel the operation because of data loss. Apparently, I should have defrag'd the drive first (I really should have thought of this before hand) 

Any ways, the question is: 
should I cancel the operation and attempt to recover the data. then buy a new drive as temporary storage?

or 

should I wait it out and hope that the operation finishes some time this week. then buy a new drive for temporary storage?

All comments are appreciated - very much

---

### Post by Mark Phelps on 2010-04-12
I have found GParted to be very s...l..o..w -- when compared to other disk partitioning utilities.  It doesn't help the timeframe in that it does it twice.

Your only choice is to wait it out.  IF you terminate any partitioning operation before it's done, you run the risk of corrupting the partition table.

---

### Post by geirha on 2010-04-12
The filesystem is likely fragmented, with filedata scattered across the entire disk, so gparted will have to defragment it so that all the used data is on the correct part of the disk.

Don't be a hero, just wait it out ;)

---

### Post by srs5694 on 2010-04-12
Another vote here for "wait it out." I've seen far too many posts here and on other forums (one here just a couple of days ago) from people who've interrupted resize operations only to find their files have become inaccessible. I'd therefore say that if you were to interrupt the process, you'd not only run the risk of having problems, but you'd almost certainly have problems.

If you continue with this (doing more iterations), try defragging the FAT partition after every ~150GB transfer.

---

### Post by eanema on 2010-04-12
Phew! It finished after 8 hours 20 mins... I'm definitely not a hero :)

Especially when an other hard drive is less than $100!

Thanks for the advise

---

