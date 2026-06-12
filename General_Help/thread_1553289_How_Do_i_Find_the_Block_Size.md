---
title: "How Do i Find the Block Size?"
date: 2010-08-14
forum: General Help
---

### Post by conradin on 2010-08-14
Hi All,
I want to find the block size of my filesystems. How can I do this?

---

### Post by yabbadabbadont on 2010-08-14
```
/root # dumpe2fs -h /dev/sda7 | grep -i "block size"
dumpe2fs 1.41.11 (14-Mar-2010)
Block size:               4096

```
You'll need to use sudo to run the command.

Edit: Of course, that only works with ext2, ext3, and ext4 filesystems.

---

