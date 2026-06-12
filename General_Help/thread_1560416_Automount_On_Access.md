---
title: "Automount On Access"
date: 2010-08-24
forum: General Help
---

### Post by hkyz on 2010-08-24
Hello,

Is it possible to modify /etc/fstab (or some other location), so that a filesystem is mounted automatically when its mount folder is accessed?

I don't want it to be mounted before the access. A solution would be really useful for sshfs folders.

Any help is greatly appreciated.

---

### Post by micheledm on 2010-08-25
Try adding the option "noauto" under the <options> column in /etc/fstab in the row of the partition you don't want to be mounted automatically.

---

### Post by hkyz on 2010-08-26
Thanks but I still want it to be automatically mounted when it is accessed.

---

