---
title: "Two GRUB issues"
date: 2010-07-10
forum: General Help
---

### Post by kkj.droid on 2010-07-10
Issue 1:
I have Mac OS X on a second hard drive, and GRUB/BURG detects 32-bit and 64-bit versions of OS X. Problem is, my CPU isn't x86-64, so I don't need the x64 version. Also, I have to use the BIOS to select OS X, because GRUB won't boot correctly to OS X anyway. 30_OS_Prober detects them despite all my efforts. Is there any way that I can block /dev/sdb boot entries?

Issue 2:
I have FreeBSD on /dev/sda3 and GRUB won't autodetect it. It's under 40_Custom, but still won't appear.

---

### Post by john newbuntu on 2010-07-11
Please add the following line to /etc/default/grub. (i.e, from a terminal, enter: gksudo gedit /etc/default/grub)

**GRUB_DISABLE_OS_PROBER="true"**

Save the file and run "sudo update-grub" on the command line.  See if that helps.

---

