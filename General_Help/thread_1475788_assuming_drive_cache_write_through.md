---
title: "assuming drive cache: write through"
date: 2010-05-07
forum: General Help
---

### Post by 98cwitr on 2010-05-07
Everytime I boot I get:

assuming drive cache: write through
assuming drive cache: write through
assuming drive cache: write through

three times and it points to my external usb drive. Any tell me how to make my box stop doing this? BIOS is set not to boot to USB btw.

there is an active bug report on it, but no resolution as of now.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440475](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440475)

---

### Post by dino99 on 2010-05-07
sudo update-pciids && update-usbids

---

### Post by q.dinar on 2011-12-12
i have installed debian 6.0.3 without desktop, and i log in as root, connect usb flash drive, and see 2 this messages, press ctrl+c to get command prompt back, and see that flash drive's led flashes and flashes. if i mount it, i can list files in it, but its led flashes, if i unmount it, it still flashes.
update-pciids
and
update-usbids
commands have not fixed this.

---

