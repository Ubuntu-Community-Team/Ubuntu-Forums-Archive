---
title: "Failed to run depmod; bus error"
date: 2009-07-11
forum: General Help
---

### Post by hmich176 on 2009-07-11
I'm having a problem here, which I'm looking for help with.  

I'm trying to run the update manager, and it gives me an error.  When I go into the terminal and run sudo apt-get install -f, I get this (which replicates the error in update manager):
```
harry@harry-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I tried to run sudo depmod -a it gave me this:
```
harry@harry-laptop:~$ sudo depmod -a
[sudo] password for harry: 
Bus error
```

Is there any solution to this problem other than reinstalling Ubuntu using a Live CD?  Personally, I'd like to learn how to fix it without the Live CD.

EDIT: 
I also tried to remove the kernel.  Here's the code for that:
```
harry@harry-laptop:~$ sudo apt-get remove linux-image-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic linux-image-2.6.28-13-generic linux-image-generic
  linux-restricted-modules-2.6.28-13-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 98.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 280609 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.28-13-generic ...
Bus error
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.28-13-generic
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-image-generic ...
Removing linux-image-2.6.28-13-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

