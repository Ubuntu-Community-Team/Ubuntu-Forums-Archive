---
title: "media tomb? in 11-08-26"
date: 2011-08-25
forum: General Help
---

### Post by Arminius on 2011-08-25
I've tried everything, mediatomb, is up and running the problem is that the one drive I have to run NTFS, refuses to share permissions, in the group category, when I move from none to "create and delete files" it will instantly move back to none, it's the last hold over from letting me create my media center, so if anyone had any ideas other then moving away from NTFS for this hard drive???

---

### Post by CatKiller on 2011-08-25
How have you mounted it?

---

### Post by Arminius on 2011-08-25
ummmm I've mounted it the default way it always mount's on ubuntu?

---

### Post by CatKiller on 2011-08-25
The default way is that it isn't mounted.

NTFS can't handle the UNIX permissions, which is why you can't change them & why you need to adjust the way it's mounted to get the permissions that you want. A suitable entry in /etc/fstab should sort you out. There are a number of tutorials to tell you what to put in there to mount an NTFS position read-and-write.

---

