---
title: "Launcher help"
date: 2011-02-17
forum: General Help
---

### Post by lord_exile on 2011-02-17
I am trying to make a custom launcher that will format a internal storage hard drive. Can anyone please help me. I store a lot of content on this drive for work and it changes every week and this will help me delete it fast instead of doing it the regular way.

---

### Post by TeoBigusGeekus on 2011-02-17
Instead of formatting it (and thus fiddling with fdisk, mkfs, fsck) you could create a launcher that deletes everything from it
```
rm -r /media/mountpointofdisk/*
```

---

