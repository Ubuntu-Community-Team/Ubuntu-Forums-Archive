---
title: "md0 mounting as read only"
date: 2010-01-02
forum: General Help
---

### Post by miromiro on 2010-01-02
After a power outage this morning, my system (RAID1, 9.10 - 32) mounts the root filesystem as read only:

```
/dev/md0 on / type ext3 (rw,errors=remount-ro)
```

I used the system rescue cd to run fsck and it showed no errors on md0. And it still mounts ro.

Is there anything that I am missing?

#edit

Solved by # touch /forcefsck

---

