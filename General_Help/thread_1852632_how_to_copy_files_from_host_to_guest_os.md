---
title: "how to copy files from host to guest os ?"
date: 2011-09-30
forum: General Help
---

### Post by naved ..... on 2011-09-30
hi i need to copy files from my host ie win7 to my guest os ie ubuntu i m using virtual box , can any 1 tell me how to do that 
i have shared folder but nothing seems to be working 
please help

---

### Post by foureyesboy on 2011-09-30
Install Virtualbox Guest Additions on the guest OS
```

$ mkdir mnt
$ sudo mount -t vboxsf -o uid=`id -u`,gid=`id -g` <sharename> mnt

```


For details refers to the steps provided in the Help on Shared folder section.

---

