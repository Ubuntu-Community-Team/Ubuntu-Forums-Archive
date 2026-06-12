---
title: "Internal ext3 drive reporting wrong &quot;used&quot; space"
date: 2009-10-13
forum: General Help
---

### Post by hypernihl on 2009-10-13
Hi All,

I'm using UBUNTU 9.04 32-bit on an Intel box. 

I have an internally mounted ext3 formatted drive which is backed up on to an NTFS formatted external drive. On the ext3 drive I see this contradiction (no issue with the NTFS backup drive, it's reporting the correct disk usage),

[IMG]http://i209.photobucket.com/albums/bb176/hypernihl/pic.png[/IMG]

Contents: 432.7 GB
Used: 457.3 GB

Where the heck did 25 GB go? I deleted all the hidden folders (.*) and remounted the drive. There are two directories on each drive, and they are each the same size. 

Any one have a clue as to why there is a 25 GB difference between the two drives? gParted shows this drive as having 25 GB of free space???

Thanks for any help on this,

-hn

---

### Post by hypernihl on 2009-10-15
any one????

---

### Post by hypernihl on 2012-01-14
Per default ext3 reserves some blocks for root. tune2fs -m 0 /dev/yourpartition sets the reserved blocks to zero.

Thanks

---

