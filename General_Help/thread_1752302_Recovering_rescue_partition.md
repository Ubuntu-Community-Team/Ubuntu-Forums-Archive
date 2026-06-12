---
title: "Recovering rescue partition"
date: 2011-05-07
forum: General Help
---

### Post by serlex on 2011-05-07
Hi,

I have installed Ubuntu (natty) on my Samsung Q320 laptop, however I can no longer access Samsung Recovery (F4 key). Is there any way I can access the reserved partition? or recover my Windows Install? Unfortunately Samsung doesn't provide any Windows CDs with laptops, as this "recovery" partition is the only way

Regards

---

### Post by serlex on 2011-05-08
anyone?

fdisk:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1958    15727603+  83  Linux
/dev/sda2   *        1959        1972      102400    7  HPFS/NTFS
/dev/sda3            1972       31259   235253906+   7  HPFS/NTFS
/dev/sda4           31260       60801   237296115    5  Extended
/dev/sda5           31260       60801   237296083+  83  Linux

```

---

