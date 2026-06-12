---
title: "nfs-kernel-server"
date: 2010-03-26
forum: General Help
---

### Post by kakamr2000 on 2010-03-26
I am relatively new to ubuntu and linux, but I have a good Unix background.  On an ubuntu 9.10 machine today I removed the nfs-kernel-server (not a smart move in hindsight).  After rebooting it cannot mount the root file system.  I have the machine booted on an ubuntu 8.04 cd.  I have mounted /dev/sda1 to /mnt.  How do I get nfs-kernel server back on the hard drive?

thanks

---

### Post by Ayuthia on 2010-03-26
You can try:
```

sudo mount -t proc none /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo cp /etc/resolv.conf /mnt/etc/
sudo chroot /mnt /bin/bash
apt-get update
apt-get install nfs-kernel-server

```
That should get you into your system and install nfs-kernel-server.  Hope that helps.

---

### Post by kakamr2000 on 2010-03-29
I tried this over the weekend, but it did not work.  All the commands work, but when I try to reboot it cannot find the boot partition.  Anything else I might be able to try?

thanks,

Kevin

---

