---
title: "boot problem"
date: 2012-06-01
forum: General Help
---

### Post by ajitesh on 2012-06-01
yesterday i installed ubuntu 12.04 alongwith my windows 7 using usb.The problem is that at the timeof booting computer is not showing the option of ubuntu instead it is running windows 7 by default.but when i insert usb,then it ask me to select 1 from ubuntu or windows 7..what shuould i do to get this option even without putting usb?

---

### Post by wilee-nilee on 2012-06-01
> **ajitesh said:**
> yesterday i installed ubuntu 12.04 alongwith my windows 7 using usb.The problem is that at the timeof booting computer is not showing the option of ubuntu instead it is running windows 7 by default.but when i insert usb,then it ask me to select 1 from ubuntu or windows 7..what shuould i do to get this option even without putting usb?

Not a hard fix boot to the Ubuntu install with the stick and run this command, in the Ubuntu terminal.
```
sudo fdisk -lu
```This will identify the partitions like sda1, or sda2, or sdb1, or sdb2...etc. We just want the first three letters not the partition number.

So when you have identified the HD Ubuntu is on run these two commands and sub the third identifying letter of the HD for the X.
```
sudo grub-install /dev/sdX
```Then run
```
sudo update-grub
```Reboot without the stick and the grub menu should show.

---

