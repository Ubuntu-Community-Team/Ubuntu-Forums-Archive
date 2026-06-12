---
title: "Quick Question"
date: 2009-07-18
forum: General Help
---

### Post by RedSingularity on 2009-07-18
I just installed Xubuntu to a USB stick.  The stick is 4 gigs.  When i go to see how much space i have left it says that i installed it on a 5 gig drive.  Why is this?  

[IMG]http://img204.imageshack.us/img204/4136/54884674.jpg[/IMG]

---

### Post by lisati on 2009-07-18
My first thought is that it could be related to two different meanings to the word "gigabyte" in common use. One is the "binary gigabyte" which is calculated based on the number 1024^3, and the other meaning "decimal gigabytte" based on the number 1000^3, which gives a larger number of gigabytes.

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

---

### Post by naklinaam on 2009-07-18
I do not know xubuntu so this might be wrong...

I recently read about "sparse files".
What "efficient" filing systems do is to not store a big block of empty data within a file but store some indicator of this block instead. Thus if you have a data which looks like 
abc000000(1 million zeros)def, the system stores abc<some indicator for million zeros>def.

thus the file is 1,000,006 bytes big but actualy needs only say 10 or 20 or something like that bytes. Thus allowing the disk to "store more than its capacity"

check the wiki at [http://en.wikipedia.org/wiki/Sparse_file]("http://en.wikipedia.org/wiki/Sparse_file") for more details, and a way way better explanation.

---

### Post by RedSingularity on 2009-07-18
Thanks guys.  That clears up my worry's as to something broken or amiss.

---

