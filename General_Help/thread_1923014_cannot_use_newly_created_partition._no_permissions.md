---
title: "cannot use newly created partition. no permissions"
date: 2012-02-09
forum: General Help
---

### Post by Marko90 on 2012-02-09
i just created an Ext2 filesystem partition with gparted on ubuntu 10.10 and i cannot create folders, install programs, or do any basic things.
it tells me that i do not have a permission to do anything with it.

what should i do?

---

### Post by pqwoerituytrueiwoq on 2012-02-09
```
sudo mkdir /media/my-partition/$USER
sudo chown $USER:$USER /media/my-partition/$USER
nautilus /media/my-partition/$USER
```replace my-partition with what ever the label of the partition is
i assume it is mounted into the /media folder and not the /mnt folder

---

### Post by oldfred on 2012-02-09
+1 on pqwoerituytrueiwoq's suggestion.

You may also need permissions as well as ownership.

sudo chmod 766 /mnt/data

use whatever mount and label/name you used to create in place of /mnt and /data.

If it is a partition on your hard drive you may want to permanently mount it.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

