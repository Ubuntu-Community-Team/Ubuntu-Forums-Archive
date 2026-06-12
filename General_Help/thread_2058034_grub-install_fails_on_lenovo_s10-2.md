---
title: "grub-install fails on lenovo s10-2"
date: 2012-09-14
forum: General Help
---

### Post by jerrry94087@yahoo.com on 2012-09-14
I am trying to install Ubuntu 12.04 LTS alongside another OS into one of the partitions. I use USB stick since this machine has no floppy or CD drive.

I am getting a message just like this: [http://i.stack.imgur.com/65dgI.png](http://i.stack.imgur.com/65dgI.png)
Executing 'grub-install /dev/sdb' failed.
This is a fatal error.

console log is as follows:
Sep 14 22:56:35 ubuntu grub-installer: info: Running chroot /target grub-install --no-floppy --force "/dev/sdb"
Sep 14 22:56:39 ubuntu grub-installer: /usr/sbin/grub-setup: error: hd1 appears to contain a iso9660 filesystem which isn't known to reserve space for DOS-stype boot. Installing GRUB there could result in FILESYSTEM DESTRUCTION if valuable data is overwritten by grub-setup (--skip-s-probe disables thich check, use at your own risk).

I believe grub attempts to install on USB stick (sdb), not on the actual hard drive (sda) for some reason.

---

