---
title: "raid array seems full but there's 8 gb left"
date: 2005-01-23
forum: General Help
---

### Post by ubuntu_demon on 2005-01-23
hi,

I don't understand this df result :

/dev/md0             230728532 221633596         0 100% /mnt/opslag

So there's 8 GB left to use but the array is 100% in use. But it isn't full. I can write files on it.

anyone ?

---

### Post by ubuntu_demon on 2005-01-23
[QUOTE=demon666_nl]hi,

I don't understand this df result :

/dev/md0             230728532 221633596         0 100% /mnt/opslag

So there's 8 GB left to use but the array is 100% in use. Also I can't write any new things on it (except empty files) so it really seems full. But when I do it with sudo I can write files on it. So I don't understand!

anyone ?[/QUOTE]
 "df -i" gives :

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/md0             29310976   88938 29222038    1% /mnt/opslag

so that isn't the problem

---

