---
title: "/dev/fuse's permission changes when it reboots"
date: 2006-03-27
forum: General Help
---

### Post by csselo on 2006-03-27
Hi

I solved this problem before but I am not lucky now :)

# ls -all /dev/fuse
crw-rw----  1 root root 10, 229 2006-03-26 16:06 /dev/fuse

when I changes all rights of fuse for user configuration(like sudo chmod 777 /dev/fuse) and reboot the machine .nothing is changed ,all rights are same again.my memory says "it is an udev problem"  :)

How can I solve this ?

thanks all
ps: I wrote it before "mknod -m 666 /dev/fuse c 10 225 "

---

### Post by csselo on 2006-03-28
I solved it.

add /etc/udev/permissions.rules 

KERNEL=="fuse", NAME="%k", MODE="0XXX"

XXX= give any permission like 666

---

