---
title: "power problem during shut down error"
date: 2011-12-01
forum: General Help
---

### Post by ErikSlinger on 2011-12-01
He
For a long time I've been using Ubuntu with great success. recently however it's not working anymore.

I have the same problem as described in the thread:
[http://ubuntuforums.org/showthread.php?t=1244466](http://ubuntuforums.org/showthread.php?t=1244466)

I get the following message:
--------------
mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)
---------------------

I tried to follow the advice from this thread but after entering the second line nothing happens and sda1 is the correct partition.
sudo mkdir /mnt/ubuntu && sudo mount /dev/sda1 /mnt/ubuntu
Any help is appreciated!

---

### Post by ErikSlinger on 2011-12-15
I have the impression that the booting with CD is continuing longer now. But still no start-up...

---

