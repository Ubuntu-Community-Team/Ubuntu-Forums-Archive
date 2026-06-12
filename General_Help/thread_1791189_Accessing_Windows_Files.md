---
title: "Accessing Windows Files"
date: 2011-06-26
forum: General Help
---

### Post by Fireicee1 on 2011-06-26
Hi, my Windows 7 won't start, neither in Safe Mode or normally.  (that's another story).  I decided to try using Ubuntu to access my Windows files, but got the message saying it could not mount it.  Anyway to fix this?

---

### Post by WorMzy on 2011-06-26
Is this the same partition you installed Wubi to? If so, it's already mounted under /host. Trying to mount it again may result in an "Already mounted or busy" type error.

If you're getting some other error, post it here. If the filesystem is corrupted beyond recognition, it may be the reason why your Windows isn't booting in the first place.

---

