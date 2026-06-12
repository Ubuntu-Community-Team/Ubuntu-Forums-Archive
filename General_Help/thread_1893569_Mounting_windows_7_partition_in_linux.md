---
title: "Mounting windows 7 partition in linux"
date: 2011-12-10
forum: General Help
---

### Post by ligiopro on 2011-12-10
[http://support.microsoft.com/kb/926185](http://support.microsoft.com/kb/926185) - system restore issues when dual booting windows 7 with windows xp.
Would linux also delete those system restore points when it mounts a windows 7 partition?

---

### Post by lechien73 on 2011-12-10
To the best of my knowledge, Linux will not *delete* the system restore points.

However, because Linux doesn't use a volume snapshot driver, any modifications to the Windows 7 partition (creation and deletion of files etc.) could make existing system restore points unstable.

---

