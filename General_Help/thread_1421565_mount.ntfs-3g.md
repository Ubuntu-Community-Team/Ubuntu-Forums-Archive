---
title: "mount.ntfs-3g"
date: 2010-03-04
forum: General Help
---

### Post by karmic-koala on 2010-03-04
Can mount.ntfs and mount.ntfs-3g reside simultaneously?

Whilst accessing an external NTFS drive mount.ntfs takes up a lot of CPU. I am not sure if its mounting the drive using mount.ntfs or mount.ntfs-3g? How do I find out and if they coexist how do I make the default mount drive ntfs-3g?

---

### Post by sisco311 on 2010-03-04
mount.ntfs and mount.ntfs-3g are symlinks to ntfs-3g:
```
ls -al /sbin/mount.ntfs*
```

---

### Post by karmic-koala on 2010-03-04
> **sisco311 said:**
> mount.ntfs and mount.ntfs-3g are symlinks to ntfs-3g

DOH, I should have known ;)

---

### Post by huangweiqiu on 2010-03-04
> **sisco311 said:**
> mount.ntfs and mount.ntfs-3g are symlinks to ntfs-3g:
```
ls -al /sbin/mount.ntfs*
```

Yes,that is what i am looking for,thanks

---

