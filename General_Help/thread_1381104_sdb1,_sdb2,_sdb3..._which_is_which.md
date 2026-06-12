---
title: "sdb1, sdb2, sdb3... which is which"
date: 2010-01-14
forum: General Help
---

### Post by waleedakleh on 2010-01-14
i have an external hard disk, partitioned to 6, but i cant tell which is which?!! i had them renamed external 1 external 2 ....external 6. so which is sdb1 which is sdb2 ...... sdb6?? when i open one of them something like this is in the address bar /media/3de01bd7-ecc8-4444-89a8-cc7aed58d20c so that doesn't help
please help???

---

### Post by audiomick on 2010-01-14
The big long string of characters looks like a UUID.
try this
```
sudo blkid -c /dev/null
```
I think that will tell you what you want to know.

---

### Post by waleedakleh on 2010-01-14
thanks that helped

---

