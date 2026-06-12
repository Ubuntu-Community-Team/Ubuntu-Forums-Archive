---
title: "for crying out loud"
date: 2010-01-10
forum: General Help
---

### Post by macabro22 on 2010-01-10
Doodes! I messed up my system somehow. Everytime I install an application I get error messages related to kernel images. I tried uninstalled the package the I think has caused the damn issue, but it won't go away. Please assist me! Here's the message:

```
sudo dpkg -r linux-backports-modules-2.6.31-1 
linux-backports-modules-2.6.31-16-generic
linux-backports-modules-2.6.31-17-generic
mercutio@Gir:/etc/initramfs-tools$ sudo dpkg -r linux-backports-modules-2.6.31-16-generic linux-backports-modules-2.6.31-17-generic 
(Reading database ... 315229 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
: RESUME=/dev/sda2 is not a valid kernel version
update-initramfs: failed for /boot/initrd.img-2.6.31-16-generic
dpkg: error processing linux-backports-modules-2.6.31-16-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
dpkg: warning: ignoring request to remove linux-backports-modules-2.6.31-17-generic, only the config
 files of which are on the system. Use --purge to remove them too.
Errors were encountered while processing:
 linux-backports-modules-2.6.31-16-generic
mercutio@Gir:/etc/initramfs-tools$ sudo dpkg --purge linux-backports-modules-2.6.31-16-generic linux-backports-modules-2.6.31-17-generic 
(Reading database ... 315163 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
: RESUME=/dev/sda2 is not a valid kernel version
update-initramfs: failed for /boot/initrd.img-2.6.31-16-generic
dpkg: error processing linux-backports-modules-2.6.31-16-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-backports-modules-2.6.31-17-generic ...
Purging configuration files for linux-backports-modules-2.6.31-17-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
: RESUME=/dev/sda2 is not a valid kernel version
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
dpkg: error processing linux-backports-modules-2.6.31-17-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.31-16-generic
 linux-backports-modules-2.6.31-17-generic
mercutio@Gir:/etc/initramfs-tools$
```

---

