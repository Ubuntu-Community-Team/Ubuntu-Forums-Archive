---
title: "Ubuntu CDROM problem"
date: 2010-02-26
forum: General Help
---

### Post by anupam89 on 2010-02-26
I have just installed ubuntu 9.10 using wubi. But the problem is I can't use apt-cdrom add command. It says "E: Failed to mount the cdrom." . When I insert the cdrom it is automatically mounted in /media directory. The /cdrom directory is empty. Pls Help.

---

### Post by Mark Phelps on 2010-02-26
As you already guessed, your CDROM is automatically being mounted.  You can't mount an already mounted device a second time.

The files present on the CD will be in the media directory you already mentioned.

---

