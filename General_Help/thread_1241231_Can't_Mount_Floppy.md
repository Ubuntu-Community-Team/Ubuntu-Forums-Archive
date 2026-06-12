---
title: "Can't Mount Floppy"
date: 2009-08-15
forum: General Help
---

### Post by Bradj47 on 2009-08-15
When I put a floppy in the drive and cd to /media/floppy/ in the terminal nothing comes up. 
```

brad@rockstar:~$ cd /
brad@rockstar:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
brad@rockstar:/$ cd media
brad@rockstar:/media$ ls
cdrom  cdrom0  floppy  floppy0
brad@rockstar:/media$ cd floppy
brad@rockstar:/media/floppy$ ls
brad@rockstar:/media/floppy$ cd ..
brad@rockstar:/media$ cd floppy0
brad@rockstar:/media/floppy0$ ls
brad@rockstar:/media/floppy0$ 

```

I know the floppy drive is connected to my motherboard properly and there is power running to it because when I boot Solaris I am able to cd to /floppy and ls and see the contents. How do I read it on Ubuntu?

---

### Post by RHTopics on 2009-08-15
It is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651)

For a quick fix try this command from a terminal window:

    sudo modprobe floppy

If doing that makes your floppy drive work then to make a more permanent fix then edit the file /etc/modules and add a new line containing the word "floppy", save the file, and then reboot to make it take effect.

example:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
floppy


```
Will need adminstrator privileges to edit /etc/modules, so do the following to use gedit to edit the file:

    Run (Alt + F2) : gksu gedit /etc/modules

---

