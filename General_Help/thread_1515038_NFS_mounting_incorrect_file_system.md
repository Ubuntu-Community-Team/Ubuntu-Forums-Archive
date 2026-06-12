---
title: "NFS mounting incorrect file system"
date: 2010-06-21
forum: General Help
---

### Post by greybeard95a on 2010-06-21
No, not fs type.  I mean it's literally mounting the wrong file system.

Hi all,

My /etc/exports:
/home    atlanta(rw,sync,fsid=0)
/media   atlanta(rw,sync,fsid=0)
/mnt     atlanta(rw,sync,fsid=0)

When I log in on atlanta, and attempt to mount /media, I get /home.  Why?

Thanks!

---

