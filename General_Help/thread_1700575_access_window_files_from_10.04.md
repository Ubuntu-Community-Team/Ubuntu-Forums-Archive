---
title: "access window files from 10.04"
date: 2011-03-05
forum: General Help
---

### Post by texas.chef94 on 2011-03-05
I intended to do the moves below, ten go to places, computer and I get this busy thing so someone tell me what I am doing incorrectly

Thanks

allen@allen-laptop:~$ sudo -s
root@allen-laptop:~# /mnt/windows
bash: /mnt/windows: is a directory
root@allen-laptop:~# mount -t ntfs /dev/sda1 /mnt/windows -o "umask=022"
fuse: mount failed: Device or resource busy
root@allen-laptop:~#

---

