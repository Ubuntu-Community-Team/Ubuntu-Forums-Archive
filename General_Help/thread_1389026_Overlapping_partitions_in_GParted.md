---
title: "Overlapping partitions in GParted"
date: 2010-01-23
forum: General Help
---

### Post by beatlesfan94 on 2010-01-23
I'm trying to re-size my media partition to a larger size. I previously re-sized other partitions to make unallocated space and that worked fine. But when I try to re-size the media partition, it says there are overlapping partitions and there's also another message about "this partition being XX blocks already. Nothing to do!" Yet it still shows the unallocated space.

How can I fix this?

Here's the output of fdisk -l by the way:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8824    70878748+  83  Linux <MEDIA
/dev/sda2   *       23484       26671    25600123+  83  Linux <LINUX MINT, MY MAIN OS
/dev/sda3           26672       29858    25599577+   7  HPFS/NTFS <VISTA
/dev/sda4           29859       30394     4305420    5  Extended
/dev/sda5           29859       30394     4305388+  82  Linux swap / Solaris <PART OF THE EXTENDED PARTITION

---

### Post by garvinrick4 on 2010-01-23
> **beatlesfan94 said:**
> I'm trying to re-size my media partition to a larger size. I previously re-sized other partitions to make unallocated space and that worked fine. But when I try to re-size the media partition, it says there are overlapping partitions and there's also another message about "this partition being XX blocks already. Nothing to do!" Yet it still shows the unallocated space.

How can I fix this?

Here's the output of fdisk -l by the way:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8824    70878748+  83  Linux <MEDIA
/dev/sda2   *       23484       26671    25600123+  83  Linux <LINUX MINT, MY MAIN OS
/dev/sda3           26672       29858    25599577+   7  HPFS/NTFS <VISTA
/dev/sda4           29859       30394     4305420    5  Extended
/dev/sda5           29859       30394     4305388+  82  Linux swap / Solaris <PART OF THE EXTENDED PARTITION
How big is your drive it looks like 35 gig in sda1 12 gig in sda2 and sda3 Vista 12 gig
sda4 is extended 2 gig and the same size as swap where it resides. That is the 4 primary.
about 71 gig and you got about 50 gig unallocated between sda1 and 2 for a total of 120 or so gig is that right? Why is the extended partition not larger by 12 gig or so and include Mint and swap? Making only 3 primary and allocate all the rest to MEDIA. Which would make sda1 about 85 gig.

---

### Post by beatlesfan94 on 2010-01-23
Here's a picture of what Gparted looks like because it'll be easier than trying to explain it in words.

[IMG]http://img62.imageshack.us/img62/263/gparted.png[/IMG]

---

### Post by garvinrick4 on 2010-01-24
> **beatlesfan94 said:**
> Here's a picture of what Gparted looks like because it'll be easier than trying to explain it in words.

[IMG]http://img62.imageshack.us/img62/263/gparted.png[/IMG]
I gave you exactly half of what you have. I see Windows is in an extended instead of a primary and swap is in extended by its lonesome so all 4 primarys are used. Do not think I have ever seen Windows in extended? Seen extended with numorous logicals inside of extended for Linux's and swaps but not ntfs in extended. Unless that is wrong why should you not be able to extend the primary partition of ext3 media sda1. Sorry going to have to investigate your scheme looks odd to me. Your "sudo fdisk -l" being an small L and without quotes.  it show's sda3 as ntfs? Has sda3 always been in that location in an extended partition? I just seem to have the feeling that that is the odd ball in the group and Vista without the D: drive partition which would be to many primary anyway. Yet they all boot fine. If you have enough RAM on board sda4 and sda5 are redundant. This is worth more investigating. Something just feels wrong here but aqain I have never seen NTFS in extended but in gparted it is extended.

---

### Post by louieb on 2010-01-24
looks like sda1 is locked - is it mounted? right click and select unmount .

---

### Post by garvinrick4 on 2010-01-24
> **louieb said:**
> looks like sda1 is locked - is it mounted? right click and select unmount .

beatlesfan94 did that fix your problem? Mark as Solved if did, I am curious as to your problem.

---

