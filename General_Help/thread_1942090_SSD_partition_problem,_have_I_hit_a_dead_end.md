---
title: "SSD partition problem, have I hit a dead end?"
date: 2012-03-16
forum: General Help
---

### Post by cNicely on 2012-03-16
Searched forums, found answer. Derp

---

### Post by pqwoerituytrueiwoq on 2012-03-16
if windows does tot see the drive it must be a driver issue in windows (or the ssd is unpluged which i sinuously doubt)
you may want to google windows [VERSION] [SSD Name/Model]

you really should use the [FONT=Courier New]noatime[/FONT] and [FONT=Courier New]nodiratime[/FONT] option in fstab since you are using a ssd with a ext4 partition
from my stab
```
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4   discard,errors=remount-ro,noatime,nodiratime 0       1
```
discard enables trim in ubuntu 10.10 and up (10.04 can unse maveric's backpacked kernel)

---

