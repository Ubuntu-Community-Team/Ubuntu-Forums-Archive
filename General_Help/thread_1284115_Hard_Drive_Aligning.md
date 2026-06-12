---
title: "Hard Drive Aligning"
date: 2009-10-06
forum: General Help
---

### Post by underwog on 2009-10-06
Learned something new today, but now I'm curious, how does Ubuntu handle this?

Here is a page on aligning:
[http://msdn.microsoft.com/en-us/library/dd758814.aspx](http://msdn.microsoft.com/en-us/library/dd758814.aspx)


Did a quick google search and the results suggested Linux may also have this problem. Thanks in advance for any insight.

---

### Post by louieb on 2009-10-06
Thats an awful read - lol -  anyway take a look at the man pages for **hdparm**

Parted and Gparted by default will align new partitions on cylinder boundaries. Which according to the MS article is an important factor in the performance when using a raid array.

---

### Post by psusi on 2009-10-07
There is absolutely no reason to align partitions to cylinder boundaries these days because there is no such thing as a cylinder any more.  The bios still pretends for compatibility with older software that expects to use cylinder/sector/head geometry, but it's fake.

Just the same, by default, partitions are still aligned this way.

---

### Post by shaggy999 on 2009-10-07
> **psusi said:**
> There is absolutely no reason to align partitions to cylinder boundaries these days because there is no such thing as a cylinder any more.  The bios still pretends for compatibility with older software that expects to use cylinder/sector/head geometry, but it's fake.

Just the same, by default, partitions are still aligned this way.

Never used an SSD drive, have you? Aligning a partition along certain boundaries can increase the life and performance of an SSD drive. Most SSD drives out there will write out to something like a 512-byte block (it's different per drive & manufacturer). Even if you're only changing a single bit the whole 512-bytes has to be re-written. Given the limited number of writes on an SSD it is wise to byte-align your partitions and ensure the block size of your partitions is the same size as the blocks on your drive. This gets rid of scenarios where a single chunk of data that should fit on a single physical block to get written to two physical blocks resulting in faster wearing out of the drive.

For more info: [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)

---

