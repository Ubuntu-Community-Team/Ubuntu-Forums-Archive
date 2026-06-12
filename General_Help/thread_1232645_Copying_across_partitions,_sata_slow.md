---
title: "Copying across partitions, sata slow?"
date: 2009-08-05
forum: General Help
---

### Post by jacobezzell on 2009-08-05
I repartitioned my 500gb sata drive to have a /storage partition and have that mounted and working well, but trying to copy all the data from my, now smaller, boot partition is going agonizingly slow.  I'm only getting 5mb/second transfer rates, that seems absurd.  Sata should be able to pull 180mb/second or so read/write, so maybe half that seems reasonable for duplicating data on the same drive... doesn't it?

---

### Post by XCan on 2009-08-06
Your regular sata drive can pull perhaps 50 MB/s read/write, in either case it is nowhere close to the bandwidth of the interface (which is the point). In your case you are both reading and writing from the same drive, which will involve tons of respositions on the head. I guess that is the reason it is going so slow, especially if you want to read from the outer parts of the drive to write to the inner parts.

---

