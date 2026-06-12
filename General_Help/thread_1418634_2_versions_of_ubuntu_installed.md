---
title: "2 versions of ubuntu installed?"
date: 2010-02-28
forum: General Help
---

### Post by jose1986 on 2010-02-28
So I have 2 versions of ubuntu installed on my computer, how can I delete the older version, which the last version installed?  Without ruining my grub because I deleted the partition but had to reinstall it because grub was running through the newest installation for some reason.  So I have ubuntu 9.10, windows 7, ubuntu 9.04 operating systems on my laptop.  Those are the order that they were installed.

---

### Post by Ozymandias_117 on 2010-02-28
I would suggest just deleting the partition of the one you don't want, using gparted on a live cd to expand whichever partition you want the space to go to, then follow this guide if the one you deleted was the one GRUB was running from: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by dcstar on 2010-02-28
> **jose1986 said:**
> So I have 2 versions of ubuntu installed on my computer, how can I delete the older version, which the last version installed?  Without ruining my grub because I deleted the partition but had to reinstall it because grub was running through the newest installation for some reason.  So I have ubuntu 9.10, windows 7, ubuntu 9.04 operating systems on my laptop.  Those are the order that they were installed.

Simply re-install Grub to use the 9.10 partition. Do a forum search on reinstalling grub for detailed instructions.

---

