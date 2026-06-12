---
title: "Mounting Hard Drives In Ubuntu 9.10"
date: 2009-12-17
forum: General Help
---

### Post by accooper on 2009-12-17
Anyone know how to get Ubuntu 9.10 to automaticly mount all hard drives on start up?  9.o4 would but I cannot get 9.10 to.

Andrew

---

### Post by lmarmisa on 2009-12-17
The **/etc/fstab** file lists the partitions that are automatically mounted at startup.

Check with the command **mount** if those partitions listed in fstab are mounted.

---

