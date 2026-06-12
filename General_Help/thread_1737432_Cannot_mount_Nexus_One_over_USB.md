---
title: "Cannot mount Nexus One over USB"
date: 2011-04-23
forum: General Help
---

### Post by Pioden on 2011-04-23
Hi folks

I hope someone can give me a little help with this. I recently rooted my Nexus One and upgrade to Android 2.3. Since the upgrade I cannot access the phones SD card over USB!!! 

Is this normal?

The phone is detected by Ubuntu - lsusb shows the Nexus One is dectected just fine.

Disk utility shows the device as sdd - but it is not mounted as sdd1 :-/

Delving a little deeper ...

root@shogun:~# file -s /dev/sdd
/dev/sdd: writable, no read permission

No read permission?!! Can anyone suggest what's going on here? A permissions issue after rooting? That's my guess. Any help/  advice appreciated.

Cheers

Huw

---

