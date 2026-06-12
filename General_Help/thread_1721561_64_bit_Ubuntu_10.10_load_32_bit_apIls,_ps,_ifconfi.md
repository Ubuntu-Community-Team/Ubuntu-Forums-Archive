---
title: "64 bit Ubuntu 10.10 load 32 bit apI:ls, ps, ifconfig after reboot"
date: 2011-04-04
forum: General Help
---

### Post by changyh on 2011-04-04
After I reboot ubuntu 10.10 64 bit, I got the following error msg:

-bash: /bin/ls: No such file or directory

===================
I did more and get the following:

$ file /bin/ls
/bin/ls: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.0.0, stripped
---------------------
It is as same as ps, ifconfig , 
/sbin/ttyload, 
/sbin/ttymon,
/usr/bin/find:                                   
/usr/bin/md5sum                                 
/usr/bin/pstree                                
/usr/bin/top
/boot/memtest86+_multiboot.bin

---

### Post by changyh on 2011-04-05
Maybe it is virus in ubuntu 10.10 64 bit

---

