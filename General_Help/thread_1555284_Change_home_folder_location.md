---
title: "Change home folder location"
date: 2010-08-17
forum: General Help
---

### Post by Winalways on 2010-08-17
As a precaution to protect my home folder contents when I reninstall  ubuntu if need arises I intend to change my home folder location to a  mounted ntfs partition in my HDD. How can I do it the GUI way? Like in  windows the "My Documents" location can be changed by going to "My  Document" properties and entering the new location.

---

### Post by ercferret18 on 2010-08-17
you can link your home directory to the other directory.

```
sudo ln -s <new home location> /home/user
```

---

### Post by oldfred on 2010-08-18
You can link NTFS partitions into /home, but cannot use a windows format for linux system partitions including /home. Windows partitions do not support file permissions & ownership that are fundamental to linux. Any data copied to a NTFS or FAT may lose permissions & ownership & you will have to manually reset if you copy back to /home.

---

