---
title: "After installing ati mobility 3470 drivers - system is died"
date: 2010-03-11
forum: General Help
---

### Post by Lolu on 2010-03-11
Hi, sorry my english

I want to switch on extra effect in Ubuntu 9.10 and system asked me whether I want to install the drivers . Then reboot and.... neither Ubuntu nor Ubuntu recovery mode dont start.

I read that in order to uninstall these drivers simply use the command:

sudo dpkg-reconfigure -phigh xserver-xorg

but I have no idea how to get into the system or the command line.

Can you help with this guys?

---

### Post by Mark Phelps on 2010-03-11
See the instructions in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Lolu on 2010-03-11
Thanks! Instruction from your link with "chroot" from LiveCD worked :)

---

