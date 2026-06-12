---
title: "Path to memory card"
date: 2009-08-06
forum: General Help
---

### Post by The-ITu on 2009-08-06
hello!
ubuntu will not start up becuse my computer can not seam to handle ubuntu 9 so I want to downgread to ubutun 8.10.
however, I want to back up all my files on a memory card from safe mode first.
i know you have use:
```
sudo mv /home/username **path to directory**
```, but the only problem is, is that I don't know what the path to a memory card is.

Thank you in advanced for helping (if you do, that is.)
_The-ITu_

---

### Post by Mka on 2009-08-06
The path to memory card on Ubuntu is /media/memory-card-label or /media/disk . Use df to see if it is mounted. If not you can mount it by yourself like:
```
mkdir /tmp/mount-point
sudo mount /dev/disk/by-label/memory-card-label /tmp/mount-point
sudo mv /home/username /tmp/mount-point

```

---

