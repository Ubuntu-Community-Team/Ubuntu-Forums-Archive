---
title: "Create partition table from terminal"
date: 2010-05-20
forum: General Help
---

### Post by Neds Moar Salt on 2010-05-20
Can it be done?  If so, how?  As far as I know it doesn't work like mkfs.ext3 and all that.

---

### Post by dcstar on 2010-05-20
> **Neds Moar Salt said:**
> Can it be done?  If so, how?  As far as I know it doesn't work like mkfs.ext3 and all that.

```
man cfdisk
man sfdisk
```

---

### Post by srs5694 on 2010-05-20
Also fdisk and parted. If you happen to want to use GPT, look for gdisk and sgdisk instead of fdisk, sfdisk, and cfdisk.

---

