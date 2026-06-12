---
title: "Dual-boot with Hackintosh 10.6"
date: 2010-02-18
forum: General Help
---

### Post by GamePad64 on 2010-02-18
I have Ubuntu 9.04, Windows 7 and Mac OS X 10.6 (Hackintosh) installed. First I installed Windows 7, then Mac OS. It's loader installed into MBR. So, before installing Ubuntu, I ran a command:
```
dd if=/dev/sda of=/mnt/usb/macos_mbr.bin bs=512 count=1
```
Is there any way to make GRUB use the loader from this file?

---

