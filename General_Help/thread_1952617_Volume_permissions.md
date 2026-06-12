---
title: "Volume permissions"
date: 2012-04-04
forum: General Help
---

### Post by zormat on 2012-04-04
Probably a stupid question.

So I get a new hard drive, which hasn't been partitioned.  So I partition it with GParted.  Now it's owned by root and I can't do anything with it, nor figure out how to change its permissions.

---

### Post by TeoBigusGeekus on 2012-04-04
Which filesystem did you choose? (ext4, ntfs, fat32, etc)

---

### Post by zormat on 2012-04-04
ext4

---

### Post by TeoBigusGeekus on 2012-04-04
You just need to change the permission of its mount point.
Plugin your drive; its mount point will be inside your /media folder, let's say disk.
Give this
```
sudo chown -R yourusername: /media/disk
```
in a terminal.

---

### Post by zormat on 2012-04-04
Thank you, sir.

---

### Post by TeoBigusGeekus on 2012-04-04
You're welcome and don't forget to mark the thread as solved.

---

