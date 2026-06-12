---
title: "Bootloader doesn't show windows at startup"
date: 2010-09-14
forum: General Help
---

### Post by wingman1 on 2010-09-14
OK,so i just installed Ubuntu from an ISO about a year old and of course i updated it to the latest version and when i get that screen at startup where i have a choice of which version to load i get something like this: My current version, memtest, an old installation of Ubuntu and some really old versions. The problem is i also have Windows7 and Vista installed(vista really needs to go) but i don't have either of them as a choice in the bootloader. How do i get it back? Also before the update i had it on the list.

---

### Post by philinux on 2010-09-14
> **wingman1 said:**
> OK,so i just installed Ubuntu from an ISO about a year old and of course i updated it to the latest version and when i get that screen at startup where i have a choice of which version to load i get something like this: My current version, memtest, an old installation of Ubuntu and some really old versions. The problem is i also have Windows7 and Vista installed(vista really needs to go) but i don't have either of them as a choice in the bootloader. How do i get it back? Also before the update i had it on the list.

Open a terminal and run this.

```
sudo update-grub
```

If that does not work I would try reinstalling grub from a livecd.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

