---
title: "problem mounting a device"
date: 2012-02-25
forum: General Help
---

### Post by royb1972 on 2012-02-25
i installed ubuntu on one of my HD's when installing created a partition with the 'advanced partition tools' and left a NTFS partition containing my docs pic's movies etc. when i restarted ubuntu the partition couldnt be mounted. i uploded win7 and in disk managment i can see the partition but cant mount it. ubuntu tells that he has sdb & sd1
the sdb cant be mounted - ubuntu show a messege 'sdb cant be found in fstab or mtab' - i need to access my files at least recover them  (some of theme are not backedup) what should i do???

thanks ahead - roy

---

### Post by bluexrider on 2012-02-25
For NTFS access you need these packages

ntfs-config
Enable/disable write support for any NTFS devices

ntfs-3g
read-write NTFS driver for FUSE

libntfs10
library that provides common NTFS access functions

ntfsprogs
tools for doing neat things in NTFS partitions from Linux

---

### Post by Morbius1 on 2012-02-25
That's a confusing set of symptoms. For one, sdb is a physical device not a partition and a physical device cannot be mounted. Second, there is no such thing as a "sd1".

I think the best thing to do is to provide some system level information. Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```

---

