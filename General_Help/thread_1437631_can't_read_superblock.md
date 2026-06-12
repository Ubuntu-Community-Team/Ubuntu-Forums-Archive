---
title: "can't read superblock"
date: 2010-03-24
forum: General Help
---

### Post by andreasdelpaso on 2010-03-24
Hello i just installed ubuntu remix in my brother's netbook.
I try to mount  his WD external hard drive but i get:
Error mounting: mount exited with exit code 32:mount: /dev/sdb1: can't read superblock
On the other hand at my netbook (also ubuntu remix) i have no problem at all mounting it....
Can anybody please help???
Thanks in advance!

---

### Post by prodigy_ on 2010-03-24
```
sudo e2fsck /deb/sdb1
```

---

### Post by andreasdelpaso on 2010-03-25
Thanks Prodigy,
problem solved only by updating over and over again!

---

