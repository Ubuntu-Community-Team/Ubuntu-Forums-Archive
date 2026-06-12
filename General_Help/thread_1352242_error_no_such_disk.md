---
title: "error: no such disk"
date: 2009-12-11
forum: General Help
---

### Post by Dave04 on 2009-12-11
Hi, I recently installed ubuntu and it asked me to restart after an update. When I restarted an error message came up when I booted into ubuntu so I booted into windows, as I have dual boot. I searched online but couldn't find anything to resolve the problem. I decided to erase the ubuntu partition and start over again, after erasing the partitions it told me that I would need to reboot for the changes to take effect. I did but before the screen that you choose the OS you want to boot into came up it said;

GRUB loading. 
error: no such disk 
grub rescue>

Why is this coming up I completely erased the partitions is there something I've done wrong and can I correct the issue without erasing my other OS.

I am new to ubuntu so I don't know s++t about it.

Please Help

Dave

---

### Post by Woody1987 on 2009-12-12
Grub is the boot loader used to boot ubuntu, when you set up ubuntu the first time, it removed the windows bootloader and installed grub. From grub you could start windows or ubuntu. The solution is to either reinstall the windows bootloader if you want only windows using the windows cd or reinstall the ubuntu on the other partition which will reinstall grub and allow you to boot both windows and ubuntu.

---

