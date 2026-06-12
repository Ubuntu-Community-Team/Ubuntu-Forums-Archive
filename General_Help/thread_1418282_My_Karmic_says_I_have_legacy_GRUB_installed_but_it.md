---
title: "My Karmic says I have legacy GRUB installed but it shows beta on startup"
date: 2010-02-28
forum: General Help
---

### Post by hurinth on 2010-02-28
During bootup the GRUB 2 screen comes up saying this is GRUB 1.97~beta4. However if I show the version from CLI it shows different: > user@comp:~$ grub-install -v
grub-install (GNU GRUB 0.97) 

My version is Karmic allright, and it is a fresh install, no upgrade from Hardy whatsoever:> user@comp:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

I'm trying to customize the menuentries, but everytime a I run update-grub, it edits /boot/grub/menu.lst! And this file is no longer used by GRUB 2!:> user@comp:~$ sudo update-grub
[sudo] password for user:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Commenting the entries in menu.lst doesn't work as before, since its GRUB 2 entries in /boot/grub/grub.cfg the ones that prevail.

I have all the GRUB 2 directories and files in place (/etc/grub.d/ and /etc/default/grub), but there seems to be a mismatch at some point between what I can do from the OS and what it is being run at boot up. 

Any ideas?

---

### Post by hurinth on 2010-02-28
No idea why, but there was a mismatch between GRUB versions.

This is what resolved the issue:

sudo apt-get update
sudo apt-get install grub-pc
chose to keep my grub settings
edited /etc/default/grub to not show recovery options
sudo update-grub
less /etc/default/grub to verify no recovery menuentries were left

Rebooted and now I can see only the entries I like.

[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

---

