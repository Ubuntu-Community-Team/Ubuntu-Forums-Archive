---
title: "Server edition guest additions in virtualbox"
date: 2011-01-11
forum: General Help
---

### Post by JJJollyjim on 2011-01-11
Hello,

I am trying to set up Ubuntu server edition 10.10 in virtualbox (windows host). All is going well, except that I can't figure out how to install the guest additions. I know how to do it in the normal edition of Ubuntu, but when I navigate to media/cdrom, it's empty.

Thanks a lot,
Jamie :-D

---

### Post by hawkmage on 2011-01-11
Try running:
```
sudo mount /dev/cdrom /mnt
```
Look under /mnt

---

### Post by JJJollyjim on 2011-01-11
> **hawkmage said:**
> Try running:
```
sudo mount /dev/cdrom /mnt
```
Look under /mnt

Thanks :)

---

