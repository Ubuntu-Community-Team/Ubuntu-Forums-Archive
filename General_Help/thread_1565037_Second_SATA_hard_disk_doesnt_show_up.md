---
title: "Second SATA hard disk doesnt show up"
date: 2010-08-31
forum: General Help
---

### Post by grumpy.biatch on 2010-08-31
I've installed 500 GB SATA hard disk but SUSE doesnt see it. The BIOS  recognized the disk. What do I do in order to get the disk show up as  sdb.

---

### Post by Grenage on 2010-08-31
You're not getting anything listed with fdisk?

```
sudo fdisk -l
```

Assuming Suse has sudo installed; otherwise, as root.

---

