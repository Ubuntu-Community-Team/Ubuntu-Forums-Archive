---
title: "Floppy drive doesn't work for U10.04 and later"
date: 2012-03-08
forum: General Help
---

### Post by haresear on 2012-03-08
I don't use my floppy drive very often. I just noticed it wasn't working in U10.10, so I checked on older and newer Ubuntu versions. I found that it still works on U8.04 and U8.10, but doesn't work on U10.04 to U11.10. When I try to mount the floppy drive, the activity light comes on briefly, but it doesn't find any media. Anyone have a clue what could cause this? Diagnostic suggestions appreciated.

---

### Post by plucky on 2012-03-08
> **haresear said:**
> I don't use my floppy drive very often. I just noticed it wasn't working in U10.10, so I checked on older and newer Ubuntu versions. I found that it still works on U8.04 and U8.10, but doesn't work on U10.04 to U11.10. When I try to mount the floppy drive, the activity light comes on briefly, but it doesn't find any media. Anyone have a clue what could cause this? Diagnostic suggestions appreciated.

From a terminal ```
udisks --mount /dev/fd0
```


Good Luck

---

### Post by haresear on 2012-03-08
Hey, that worked! Thanks very much.

---

