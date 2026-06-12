---
title: "Failed update linux-image-2.6.12-10-686"
date: 2006-03-24
forum: General Help
---

### Post by xemre on 2006-03-24
when i want to update my system  with apt-get update && apt-get upgrade it gives some error message likes below 


(Reading database ... 87640 files and directories currently installed.)
Preparing to replace libcairo2 1.0.2-0ubuntu1 (using .../libcairo2_1.0.2-0ubuntu1.1_i386.deb) ...
Unpacking replacement libcairo2 ...
Preparing to replace linux-image-2.6.12-10-686 2.6.12-10.24 (using .../linux-image-2.6.12-10-686_2.6.12-10.30_i386.deb) ...
The directory /lib/modules/2.6.12-10-686 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.12-10-686 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.12-10-686_2.6.12-10.30_i386.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./lib/modules/2.6.12-10-686/kernel/drivers/char/watchdog/machzwd.ko': 
No space left on device
dpkg-deb: subprocess paste killed by signal (Veri al&#305;nam&#305;yor)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.12-10-686_2.6.12-10.30_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

how i can solve this.

---

### Post by dcstar on 2006-03-24
[QUOTE=xemre]when i want to update my system  with apt-get update && apt-get upgrade it gives some error message likes below 


(Reading database ... 87640 files and directories currently installed.)
Preparing to replace libcairo2 1.0.2-0ubuntu1 (using .../libcairo2_1.0.2-0ubuntu1.1_i386.deb) ...
Unpacking replacement libcairo2 ...
Preparing to replace linux-image-2.6.12-10-686 2.6.12-10.24 (using .../linux-image-2.6.12-10-686_2.6.12-10.30_i386.deb) ...
The directory /lib/modules/2.6.12-10-686 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.12-10-686 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.12-10-686_2.6.12-10.30_i386.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./lib/modules/2.6.12-10-686/kernel/drivers/char/watchdog/machzwd.ko': 
**No space left on device**
dpkg-deb: subprocess paste killed by signal (Veri al&#305;nam&#305;yor)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.12-10-686_2.6.12-10.30_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

how i can solve this.[/QUOTE]
Delete some files so your system has room to do the upgrade.

---

