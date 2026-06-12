---
title: "Ran into a new problem migrating Linux to its own partition..."
date: 2011-10-20
forum: General Help
---

### Post by Silverflyer on 2011-10-20
Was preparing to follow the instructions given in my other thread to migrate my Ubuntu from a Wubi install to its own partition.  Step one was to move everything to a new HDD, that was accomplished and I am up and running with the new HDD and Wubi install of Linux.  I used EaseUS to clone the old HDD to the new one.  I created a separate Ubuntu partition and got this message in Disk Utility.  Now what do I do, I want to fix this before migrating my Linux to the partition.

---

### Post by mikejonesey on 2011-10-20
this is cause by either a bug in gparted, a bad entry via fdisk or by using a poor quality tool... to fix i sugest you backup the files and then repartition...

---

### Post by Silverflyer on 2011-10-20
> **mikejonesey said:**
> this is cause by either a bug in gparted, a bad entry via fdisk or by using a poor quality tool... to fix i sugest you backup the files and then repartition...


Does that mean I need to start all over copying the files to this drive?

Damnit...

---

### Post by Silverflyer on 2011-10-20
> **Silverflyer said:**
> Does that mean I need to start all over copying the files to this drive?

Damnit...

  Ok, here is a question, so I downloaded the .iso of gparted and logged into it.  How do I align the partition, it gave me a few options, I have no idea which is the right option.

---

### Post by oldfred on 2011-10-20
I think this has been reported before and may not be a major issue. Is drive SSD or new 4K sector?, If not I do not think it matters.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by Silverflyer on 2011-10-20
It is a brand new Hitachi, IIRC, not an SSD.

---

### Post by oldfred on 2011-10-20
Many new drives are 4K even some that are not over 2TiB that may have to be.

---

### Post by Silverflyer on 2011-10-21
I solved it by letting the built in Partition Manager in Win Vista do the partitioning.  Moved my Wubi install flawlessly afterwards.  Thanks.

---

