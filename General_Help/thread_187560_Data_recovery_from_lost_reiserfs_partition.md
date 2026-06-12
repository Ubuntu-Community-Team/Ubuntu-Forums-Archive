---
title: "Data recovery from lost reiserfs partition?"
date: 2006-06-03
forum: General Help
---

### Post by oskar.hermansson on 2006-06-03
I have lost a whole reiserfs partition. Is it still possible to recover any data from it?

First I installed win xp on one partition. Then, when I was installing Dapper on a second partition, in the manual partitioning tool i noticed that my third partition (reiserfs) used for backup/archive was listed as unallocated disk space! I panic and cancelled the dapper installation.

Did win xp destroy my third partition?

Is there any way to recover any data from it? I figure i can't use reiserfsck because its not even listed as a partition any more, or am i wrong?

---

### Post by debernardis on 2006-06-03
Try **Foremost** from the repos or - better - from its source [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

This can restore several file types and you can configure for new file types if you can determine their header and footer sequences.

You can also try Testdisk and Photorec from [http://www.cgsecurity.org/](http://www.cgsecurity.org/) (they are not directed to reiserfs though but could restore some files).

There are also plenty of windows applications, i.e. Nucleus Kernel ReiserFS (there's a demo you can download and lets you see which files you can restore, but in order to get them you have to pay $$$ for the license), PC Inspector File Recovery, Quick Recovery for Linux, and so on.

---

### Post by oskar.hermansson on 2006-06-06
Thank you for all your suggestions! (and for helping me recover my data)

I tried Testdisk and it worked fantastic! I can really recommend it, if anyone else has lost/corrupted their partition table.

---

