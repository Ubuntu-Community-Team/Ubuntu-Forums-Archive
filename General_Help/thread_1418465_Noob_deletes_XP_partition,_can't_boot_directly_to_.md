---
title: "Noob deletes XP partition, can't boot directly to ubuntu"
date: 2010-02-28
forum: General Help
---

### Post by clark14 on 2010-02-28
I have deleted sda1, sda2 as they were XP partitions that I no longer wanted to use (yay!).  After doing so, when I rebooted I just got a blinking cursor.  I was able to boot with the Ubuntu 9.10 install CD, and found that I could elect to boot from the first hard drive, and in doing so the usual grub menu was displayed, and I could boot to my Ubuntu 9.10 partition (sda5 inside of sda3 extended partition).  So, noobid that I am, I figured I would try to 'fix' grub.  ran commands grub>root (hd0,4); grub> setup(hd0)

Now, when I reboot, it goes directly to the grub command line, no multiboot menu, and I cannot find a way to boot to my Ubuntu partition.  The partition is still there, though, as I've checked from the Ubuntu CD.  Any help would be most appreciated.

---

### Post by clark14 on 2010-02-28
Well, if at grub prompt I enter the following commands I can boot to my ubuntu partition.

grub> kernel /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5
grub> initrd /boot/initrd.img-2.6.31-19-generic
grub> boot

But how can I get it to bring up the multiboot menu with selections for different kernels?

---

### Post by themusicalduck on 2010-02-28
Once you've booted back into Ubuntu, try running ```
sudo update-grub
``` into a terminal.

---

### Post by clark14 on 2010-02-28
Yes, that did it.  Although it no longer shows the multiboot menu.  It looks like it is now using /boot/grub/menu.lst instead of /boot/grub/grub.cfg.  If anyone cares to elaborate on  why one file or the other is used, I'd love to know more.  The problem is solved though.  Thanks.

---

### Post by oldfred on 2010-02-28
I think the standard install still includes old grub, so when you reinstalled you used the commands to reinstall grub legacy to the MBR. If it works I would leave it. Otherwise you have to uninstall grub legacy and reinstall grub2.

---

