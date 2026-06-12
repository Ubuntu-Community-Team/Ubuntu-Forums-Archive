---
title: "Can't create new ext3 partition on old lvm partition"
date: 2010-11-25
forum: General Help
---

### Post by holiday on 2010-11-25
I was having trouble with an old lvm partition so I pulled all the data off and now want to re-partition it as an ordinary ext3 partition.

But gparted offers only Logical Partition for that partition. How do I convert that partition to a Primary or Extended partition - and which do I want?

Thanks

---

### Post by holiday on 2010-11-25
Ok I solved it.

I was trying to operate on the child partition. Once I deleted the parent partition, I could convert it to Primary ext3 and now all is well.

I noticed that the parent partition and the child were the same size and so...

Yes, all is well. 

Don't like LVM. Don't like LVM...

---

