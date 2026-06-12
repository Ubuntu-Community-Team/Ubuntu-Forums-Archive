---
title: "using dd i/o errors"
date: 2009-07-19
forum: General Help
---

### Post by rado3105 on 2009-07-19
Hi I want to make copy of whole disk /dev/sdb, I used dd for doing that, but it showed finished with i/o errors. Now I dont know if that image is correct. I was trying to ddrescue, but it doesnt work, propably partitions must be mounted. Can you help?

---

### Post by rbc on 2009-07-19
In terminal:
sha1sum /dev/sdb

Then do the same for the drive you cloned it to. The result will be some long hexadecimal number. If they different, then you have not created an exact copy. A word of warning, though. If the hash (sha1) results are different, there will not be an explanantion as to why. Also, running a hash (md5 or sha1) on an large hard drive takes a long time

---

