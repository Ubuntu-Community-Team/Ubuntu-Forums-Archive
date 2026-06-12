---
title: "Parted Help"
date: 2010-07-29
forum: General Help
---

### Post by jmg999 on 2010-07-29
Hi,

I'm creating a RAID 5 array of 8x500GB HDDs behind a Promise controller.  According to Promise, I have to use Parted to created a GPT partition, so Ubuntu can see the actual size of the array (3.5TB).  When creating the partition, Parted asks for the start/end of the partition table.  I've started at 1, but I'm unable to figure out the end size.  I'd like to use the entire 3.5TB array all in one partition.  Any help would be greatly appreciated.  Thank you.

---

### Post by jmg999 on 2010-07-29
I found the answer here:

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

Worked great!

---

