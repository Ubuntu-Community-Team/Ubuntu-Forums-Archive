---
title: "Mounting NFS in background"
date: 2006-02-23
forum: General Help
---

### Post by c2h5oh on 2006-02-23
The problem is I have a really big nfs on a rather slow server mounted when the system boots up, which takes about 90 seconds and I'd rather have systen continue booting up and mount nfs in background, rather than wait.

I'd like to know if there is a way I can force mounting of NFS in background by appropriate entry in fstab, or it has to be done by placing some code in bootscripts? 'bg' is not enough since it forces mounting in background starting from the second try.

---

### Post by minfo on 2006-02-25
Install portmap

---

