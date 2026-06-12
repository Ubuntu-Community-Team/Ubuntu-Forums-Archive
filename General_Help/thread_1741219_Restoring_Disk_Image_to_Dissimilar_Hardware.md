---
title: "Restoring Disk Image to Dissimilar Hardware"
date: 2011-04-27
forum: General Help
---

### Post by fleamour on 2011-04-27
In the event of theoretical anticipated motherboard failure; how would Ubuntu react to dissimilar hardware?  In that the Linux kernel contains, as I understand, all the necessary drivers.

---

### Post by ratcheer on 2011-04-27
Don't even think about it with a disk image. If you want to do something like that, you need logical backups, such as rsync would make.

Tim

---

### Post by fleamour on 2011-04-27
Like Back In Time?  So you would do fresh install then apply backup?

---

### Post by ratcheer on 2011-04-28
Well, you wouldn't exactly just "apply backup", you would selectively restore any directories or files you need.

Tim

---

