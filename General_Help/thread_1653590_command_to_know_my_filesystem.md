---
title: "command to know my filesystem"
date: 2010-12-27
forum: General Help
---

### Post by fabjoa on 2010-12-27
Howdie!

I'd like to know which command i should run from the terminal to know which file system (ext3, ext4, etc...) my Ubuntu runs on.

Thanks!

---

### Post by karthick87 on 2010-12-27
```
mount | grep ^/
```

---

### Post by VCoolio on 2010-12-27
sudo blkid
sudo fdisk -l

---

