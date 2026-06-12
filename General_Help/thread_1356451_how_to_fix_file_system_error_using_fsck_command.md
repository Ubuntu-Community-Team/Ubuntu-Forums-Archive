---
title: "how to fix file system error using fsck command"
date: 2009-12-16
forum: General Help
---

### Post by suresh_vandiyur on 2009-12-16
hi all if i started my system it shows buffer i/o error on hda5 logical block 1 to 11 and finally goes to control-D give root password maintenance. how to fix this issue. please help me.

---

### Post by sisco311 on 2009-12-16
type your root password and run:
```
e2fsck -C0 -p -f -v /dev/hda5
```

---

### Post by suresh_vandiyur on 2009-12-17
> **sisco311 said:**
> type your root password and run:
```
e2fsck -C0 -p -f -v /dev/hda5
```

Thanks. still the error occur buffer i/o error hd5 logical block 1 to 11 . if i should run above command data will be loss or not. please help.

---

