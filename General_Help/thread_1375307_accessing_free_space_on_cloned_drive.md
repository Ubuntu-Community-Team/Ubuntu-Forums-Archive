---
title: "accessing free space on cloned drive"
date: 2010-01-07
forum: General Help
---

### Post by mfox on 2010-01-07
I have an MSI Wind with Windows, Ubuntu Netbook Remix and another Ubuntu derivative installed on my 80gb drive.  I recently acquired a 160gb drive, which I plan to put into the Wind.  I cloned the 80gb drive, which left me with an identical configuration, plus 80gb of unallocated free space.  The problem is that I already have 4 primary partitions; the last of them (adjacent to the free space) is divided up into 4 extended partitions.  I tried to make the free space available in gparted, but it won't let me create a new partition because I already have 4 primaries.  Is there some way I can get this into the last primary partition?  I tried expanding the size of the extended partitions in the 4th primary partition, but gparted won't let me do this.

---

### Post by audiomick on 2010-01-07
Hallo.
Your 4th partition must be an extended with 4 logical partitions in it.
I _**think**_ you have to expand the extended, then you can expand the logicals inside it, or add another one in the free space.

---

### Post by michy99 on 2010-01-07
Can you post a screenshot from gParted? Are you running it from a live cd? You need to have all the partitions unmounted, including any swap partition.

---

### Post by teward on 2010-01-07
In order to expand the space of the logical drives, you need to expand the space of the extended partition first.

---

### Post by -kg- on 2010-01-07
> **TrekCaptainUSA said:**
> In order to expand the space of the logical drives, you need to expand the space of the extended partition first.

Exactly right.  Read the "How To Partition" pages at the link in my signature block, especially the ones on Extended Partitions and Logical partitions.

---

### Post by mfox on 2010-01-07
Stupid me!  I couldn't do anything with the unallocated space because I kept trying to incorporate it into the logical partitions that were part of the one extended partition.  Once I clicked on the extended partition itself, rather than the partitions within it, I could resize it to encompass the unallocated space.  Presumably, this was only possible because the unallocated space was adjacent to the extended partition.  For the benefit of anyone else who has a similar question, the drive looked like this before I solved the problem:

/dev/sdb1 (primary)
/dev/sdb2 (primary)
/dev/sdb3 (primary)
/dev/sdb4 (extended)
      ....../dev/sdb5
      ....../dev/sdb6
      ....../dev/sdb7
      ....../dev/sdb8
unallocated

Clicking on /dev/sdb4 and then selecting resize did the trick.  Thanks to all three of you for explaining and pointing me to the partition thread.

---

