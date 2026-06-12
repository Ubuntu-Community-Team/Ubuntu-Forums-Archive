---
title: "Partition appears twice"
date: 2010-05-03
forum: General Help
---

### Post by stevepoppers on 2010-05-03
On Ubuntu 10.04, under Places, and in the sidebar of the file browser the same partition shows up twice, as Acer and as sda1. It's my ntfs windows partition. It's mountable, and completely usable as Acer, but I can't do anything with the link sda1. Is there a way I can at least get rid of the bad link?

---

### Post by WorMzy on 2010-05-03
Do you get this error?:
```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

---

### Post by stevepoppers on 2010-05-03
Yes. It just made no sense to me because I can mount the partition with the other link and through the terminal.

---

### Post by WorMzy on 2010-05-03
I've had that problem since Karmic, but I haven't found any way to fix it, so I've learnt to just ignore it. Like you, I can mount the partition fine using it's twin.

Maybe someone else knows a solution.

---

### Post by pmulgaonkar on 2010-07-27
I have the same problem. If anyone has a solution, would love to hear it.

Thanks.

---

