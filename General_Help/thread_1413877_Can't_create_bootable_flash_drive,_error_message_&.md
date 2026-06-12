---
title: "Can't create bootable flash drive, error message &quot;No such file or directory&quot;"
date: 2010-02-23
forum: General Help
---

### Post by sadimus on 2010-02-23
Ok here's my problem. I'm trying to install windows 7 unto my netbook. The problem is I've hit a roadblock, I'm using an intel mac to prepare my flash drive so it can be bootable. I unmounted it using     diskutil unmountDisk /dev/disk2
                Unmount of all volumes on disk2 was successful   

Which you can see was succesful. Now im trying to mount the windows7.iso image unto the flash drive and i keep getting this error.  The image is on my desktop. Am  I not specifying the path properly?

sudo dd if=/home/sadiq/windows7222.iso of=/dev/disk2 bs=1m
dd: /home/sadiq/windows7222.iso: No such file or directory



Can someone point me in the right direction please???

---

