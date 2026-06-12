---
title: "How do I make a syslinux file for an ubuntu partition that isw not where syslinux is."
date: 2012-08-13
forum: General Help
---

### Post by samercier on 2012-08-13
Sorry bit of an ubuntu and syslinux n00b just wondering and couldn't find the documentation using syslinux and ubuntu as my search terms on google.

---

### Post by Cheesehead on 2012-08-13
See "man syslinux" for instructions on how to install and use it.

Generally, you should **not** install syslinux into an ext* partition. Syslinux is intended for FAT filesystems.

For example on a USB stick, one tiny partition (FAT) would have syslinux, and a second large partition (ext3) would have Ubuntu.

This is already done automatically by Startup Disk Creator and Unetbootin and Debian Live and others, so a new user shouldn't need to mess with manually installing syslinux at all.

What are you trying to really do?

---

