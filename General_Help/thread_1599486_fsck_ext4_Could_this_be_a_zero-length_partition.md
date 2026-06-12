---
title: "fsck ext4 Could this be a zero-length partition?"
date: 2010-10-17
forum: General Help
---

### Post by gabak on 2010-10-17
ubuntu 10.10
what does it mean? how can i fix it? the main problem i cant access to my hdd of 500gb
also for some reason i dont see my blu-ray-dvd either. just filesystem

desktop:~# fsck -fyv /dev/sdb1

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

---

### Post by juliobahar on 2011-11-28
> **gabak said:**
> ubuntu 10.10
what does it mean? how can i fix it? the main problem i cant access to my hdd of 500gb
also for some reason i dont see my blu-ray-dvd either. just filesystem

desktop:~# fsck -fyv /dev/sdb1

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

You might have the same problem as mine. My hard drive recently turned bad with a couple of bad sectors, I think we need a hdd replacement. A "short read error" from what searched seemed to be consistent with a bad sector.

```
sudo fsck -y /dev/sdb1
``` 
seemed to solve my problem. You have to unmount your device prior to the fsck. Tell me how things go.

---

