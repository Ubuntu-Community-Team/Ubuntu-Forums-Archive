---
title: "ACL and native ubuntu-zfs"
date: 2012-02-14
forum: General Help
---

### Post by MacUsers on 2012-02-14
Dear all,

I'm completely new in this ZFS business. Right now I'm trying out a *raidz* pool (consist of three WD 2TB drives), which mounts as */exPort* on my ubuntu server and trying to figure out how apply ACL on it. Basically, this is what I want to achieve:
```
setfacl -m g:mgroup:rw /exPort/
``` If I do that, I get: **setfacl: /exPort/: Operation not supported** for obvious reason. How can I do the same with underlaying ZFS file-system? Any help would be very much appreciated. Cheers!!

---

### Post by MacUsers on 2012-02-14
I hate to buzz, but is any one out here applied ACL to zfs/zpool or know how to do that? Cheers!!

---

