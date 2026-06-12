---
title: "Kernel uninstalled :-("
date: 2012-04-09
forum: General Help
---

### Post by vinay_wagh on 2012-04-09
Dear Forum members,

I have 12.04 (with latest updates) installed on my desktop. Yesterday by mistake, I uninstalled the kernel (my guess is I might have removed some essential lib for which kernel was a dependency). Now after reboot I dont see the Ubuntu option in grub.

I have access to the 11.10 CD, but I dont want to reinstall. Can somebody direct me?

Thanks in advance.

VInay

P.S.
Is this forum appropriate for this post?

---

### Post by grahammechanical on 2012-04-09
Some time soon a moderator will move this post to the Ubuntu+1 section of the forum because that is where we help with problems with the development release, which 12.04 still is.

Please post exactly what you see in the Grub menu. Please explain more clearly. There might be an option to boot into an earlier kernel. If you have not removed that also. But we cannot advise you unless you tell us exactly what you see on the boot menu.

Otherwise, Re-install is the answer.

Regards.

---

### Post by vinay_wagh on 2012-04-09
Thanks for your quick reply. 

Currently I can see only three options in grub:
1. Memtest 86 +
2. Memtest 86 +, serial console (I forgot the number here)
3. Windows 7

Using other bootable CD, I am actually able to mount / partition and do chroot as well. So in that case will the following work:
After chroot, if I install a package and manually add entries to grub conf file, will that affect the original installation? (I didnt want to test this without experts' opinion as it may spoil the entire system, hence I havent done anything yet.)

Regards

VInay

---

### Post by vinay_wagh on 2012-04-11
I guess reinstall seems to be the best option. The chroot and installing the package didnt work :-(

-- VInay

---

### Post by vinay_wagh on 2012-04-12
Its working, I guess yesterday there was some other problem with apt-get.

So after chroot, install linux-headers-generic, linux generic and linx-image-generic
Exit the chroot shell, unmount the partition and then reboot...

-- VInay

---

