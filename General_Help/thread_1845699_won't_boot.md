---
title: "won't boot"
date: 2011-09-17
forum: General Help
---

### Post by tomgnu on 2011-09-17
have message.....    hard drive boot error
will not boot at all, is my hard drive broken or is there anything i can try?
(ubuntu 11.04)

---

### Post by TeoBigusGeekus on 2011-09-17
Boot up with a live cd/usb, open a terminal and give
```
sudo fsck /dev/sda1
```
Replace sda1 with your boot partition.
The command will search for errors and attempt to fix them.

---

### Post by tomgnu on 2011-09-20
thanks for your help, but seems like its time for a new hd.
cant even install anything on it. 
thanks again for your time

---

