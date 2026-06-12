---
title: "mdadm RAID level migration"
date: 2011-03-05
forum: General Help
---

### Post by Barry Cent on 2011-03-05
Hi,

Would it be possible for me to change a currently working mdadm RAID1 array to a RAID0 array without recreating the filesystem on the array?

I have a backup of the data in various places on my network, but I would like to avoid recopying the data back over if at all possible.

If this is possible, can you offer any pointers on how I would achieve it?

Thanks so much.

Joe

---

### Post by chalex on 2011-03-05
No, not possible.  Make a backup, make the new array/filesystems, restore from backup.

---

