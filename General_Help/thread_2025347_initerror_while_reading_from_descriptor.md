---
title: "init:error while reading from descriptor"
date: 2012-07-14
forum: General Help
---

### Post by rockanjan on 2012-07-14
Hi,
I have Ubuntu 12.04 (upgraded from 11.10). Few days back, while trying to install a new software, it gave me an error that libc.6.so is not the newest version. I had libc-2.13.so but it required libc-2.15.so. I tried removing libc-2.13.so to add the new one at the location /lib/x86_64-linux-gnu, and the system halted. Then, from the live boot, i managed to add the newest library and create the symbolic link libc.so.6. I did a quick reboot hoping the problem was solved. However, after loading ubuntu from the grub, the system halts showing the following error:

init: error while reading from descriptor: bad file descriptor

Can anyone help how to solve this problem?

---

