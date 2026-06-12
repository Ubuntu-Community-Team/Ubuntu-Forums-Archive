---
title: "&quot;Read only filesystem&quot; problem"
date: 2010-08-03
forum: General Help
---

### Post by jl2035 on 2010-08-03
My hd is split in two partitions, ubuntu filesystem and this storage partition which is just useless. I can't write to it, I can't move or delete files... It says "Read only File system". Whatever I change in the "Storage device manager" application, changes back to default automatically.

Please help me!

---

### Post by prodigy_ on 2010-08-03
More info needed: where the storage partition is located, what kind of file system it uses, etc. So you start trobleshooting with the following commands (in Teminal): ```
cat /etc/fstab
mount
sudo fdisk -l
```
Post the output here.

---

### Post by jl2035 on 2010-08-04
Ok this looks weird... Everything works now, although I didn't make any changes to /etc/fstab. I just deleted "Storage device manager" application, and now I can create and delete files. Thanks for your help anyway...

---

