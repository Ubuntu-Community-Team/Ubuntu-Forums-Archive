---
title: "How to reset home partition address address"
date: 2009-10-12
forum: General Help
---

### Post by aum11 on 2009-10-12
Since changing home partition from ext3 to ext4, 9,04 has been unable to find the home partition.

The partition is fine and can be accessed from karmic.

So how do I reestablish home address please.

---

### Post by P4man on 2009-10-12
Just add it to your fstab. e.g.

```
UUID=b79d9021-e273-4ad4-94b1-cd39d9eb923d  /home  ext4 defaults    0  2  
```

(obviously change the UUID and partition type to the one of your partition. To find out, enter "sudo blkid" in a terminal).

---

### Post by aum11 on 2009-10-12
P4man...thanks so much..you saved me hours of work.

---

