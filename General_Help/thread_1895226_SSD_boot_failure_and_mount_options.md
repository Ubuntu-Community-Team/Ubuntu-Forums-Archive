---
title: "SSD boot failure and mount options"
date: 2011-12-14
forum: General Help
---

### Post by Bobhuber on 2011-12-14
Hey All
I just installed an SSD drive and after extensive googling have it partitioned,aligned and 11.10 installed.
The problem I've found and I guess I'm not alone is that if you set up the drive without  journeling (as recommended) and attempt to set data=writeback  in fstab  it fails on reboot. If I remove the statement from the mount options on the drive all works fine. Need some expert advice on this one. I saw some posts on Fedora that it's directly related to the 3.0 Kernel ?? Here's the fstab mount options that are working without the writeback statement.
```
UUID=578add39-4eb1-4ace-8648-fb46de65cc9d /    ext4   noatime,discard,user_xattr,acl,errors=remount-ro  0       1
```

---

