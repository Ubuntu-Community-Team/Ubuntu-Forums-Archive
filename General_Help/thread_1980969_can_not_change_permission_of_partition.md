---
title: "can not change permission of partition"
date: 2012-05-16
forum: General Help
---

### Post by chaopoch on 2012-05-16
I am using Ubuntu 12.04 and trying to change the permission of partition, but fail to make it. I never experienced problem like this in previous versions, thank for help.

chang@chang-F3JC:~$ sudo chown chang:chang /media/sda1
chown: changing ownership of `/media/sda1': Read-only file system

[ATTACH]218056[/ATTACH]

[ATTACH]218057[/ATTACH]

---

### Post by 2F4U on 2012-05-16
Why would you change the ownership of the whole partition? My understanding is that chown changes file and folder ownerships. Additionally, the partitions seems to be mounted read-only.

---

### Post by chaopoch on 2012-05-16
Thanks for reply,

Don't know what is going on?

I reboot the computer and the partition is now normal to create and paste files and folders.

---

