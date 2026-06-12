---
title: "kernal corrupted"
date: 2009-12-29
forum: General Help
---

### Post by philp01 on 2009-12-29
Hi,

Recently, I lost the ability to boot into the 2.6.31-16 with an error about the kernel.  I am able to boot into the 2.6.31-14 version.  Is there a way to re-install the *-16 kernel without a completely new re-installation?  This appears to have happened after an update that I approved.  I was sure to wait for the installation to complete but perhaps the kernel was still being updated when I shut down?

If it helps, this is what my /boot directory looks like:
-rw-r--r-- 1 root root 3941696 2009-10-16 11:12 vmlinuz-2.6.31-14-generic
-rw-r--r-- 1 root root 2130808 2009-10-16 11:12 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root  105768 2009-10-16 11:12 config-2.6.31-14-generic
-rw-r--r-- 1 root root  623709 2009-10-16 11:12 abi-2.6.31-14-generic
-rw-r--r-- 1 root root    1336 2009-10-16 11:18 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root  128796 2009-10-23 11:24 memtest86+.bin
-rw-r--r-- 1 root root 3941984 2009-12-08 00:08 vmlinuz-2.6.31-16-generic
-rw-r--r-- 1 root root 2131522 2009-12-08 00:08 System.map-2.6.31-16-generic
-rw-r--r-- 1 root root  105768 2009-12-08 00:08 config-2.6.31-16-generic
-rw-r--r-- 1 root root  623709 2009-12-08 00:08 abi-2.6.31-16-generic
-rw-r--r-- 1 root root    1336 2009-12-08 00:14 vmcoreinfo-2.6.31-16-generic
-rw-r--r-- 1 root root 8140143 2009-12-15 18:02 initrd.img-2.6.31-14-generic
drwxr-xr-x 2 root root    4096 2009-12-15 19:30 grub
-rw-r--r-- 1 root root 8139675 2009-12-28 14:30 initrd.img-2.6.31-16-generic

Thanks in advance for any help or suggestions.
Phil

---

### Post by dcstar on 2009-12-30
> **philp01 said:**
> Hi,

Recently, I lost the ability to boot into the 2.6.31-16 with an error about the kernel.  I am able to boot into the 2.6.31-14 version.  Is there a way to re-install the *-16 kernel without a completely new re-installation?  This appears to have happened after an update that I approved.  I was sure to wait for the installation to complete but perhaps the kernel was still being updated when I shut down?

If it helps, this is what my /boot directory looks like:
-rw-r--r-- 1 root root 3941696 2009-10-16 11:12 vmlinuz-2.6.31-14-generic
-rw-r--r-- 1 root root 2130808 2009-10-16 11:12 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root  105768 2009-10-16 11:12 config-2.6.31-14-generic
-rw-r--r-- 1 root root  623709 2009-10-16 11:12 abi-2.6.31-14-generic
-rw-r--r-- 1 root root    1336 2009-10-16 11:18 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root  128796 2009-10-23 11:24 memtest86+.bin
-rw-r--r-- 1 root root 3941984 2009-12-08 00:08 vmlinuz-2.6.31-16-generic
-rw-r--r-- 1 root root 2131522 2009-12-08 00:08 System.map-2.6.31-16-generic
-rw-r--r-- 1 root root  105768 2009-12-08 00:08 config-2.6.31-16-generic
-rw-r--r-- 1 root root  623709 2009-12-08 00:08 abi-2.6.31-16-generic
-rw-r--r-- 1 root root    1336 2009-12-08 00:14 vmcoreinfo-2.6.31-16-generic
-rw-r--r-- 1 root root 8140143 2009-12-15 18:02 initrd.img-2.6.31-14-generic
drwxr-xr-x 2 root root    4096 2009-12-15 19:30 grub
-rw-r--r-- 1 root root 8139675 2009-12-28 14:30 initrd.img-2.6.31-16-generic

Thanks in advance for any help or suggestions.
Phil

Go into Synaptic and mark the appropriate packages for re-installation.

---

### Post by upbeat.linux on 2009-12-30
If you are running the desktop version you should be able to boot into the kernel that works, launch Synaptic, search for the bad kernel, remove it, then reinstall it.

---

### Post by philp01 on 2009-12-30
Thank you both for the tips.  I'll try that later today.

Phil

---

