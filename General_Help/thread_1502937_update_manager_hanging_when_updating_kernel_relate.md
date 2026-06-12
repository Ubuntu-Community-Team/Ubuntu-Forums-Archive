---
title: "update manager hanging when updating kernel related stuff"
date: 2010-06-06
forum: General Help
---

### Post by fishacre on 2010-06-06
Update manager popped up with some kernel related update this morning, and now it's hanging:

Selecting previously deselected package linux-image-2.6.32-22-generic.
(Reading database ... 224417 files and directories currently installed.)
Unpacking linux-image-2.6.32-22-generic (from .../linux-image-2.6.32-22-generic_2.6.32-22.36_amd64.deb) ...
Done.
Preparing to replace linux-generic 2.6.32.21.22 (using .../linux-generic_2.6.32.22.23_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.32.21.22 (using .../linux-image-generic_2.6.32.22.23_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.32-22.
Unpacking linux-headers-2.6.32-22 (from .../linux-headers-2.6.32-22_2.6.32-22.36_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-22-generic.
Unpacking linux-headers-2.6.32-22-generic (from .../linux-headers-2.6.32-22-generic_2.6.32-22.36_amd64.deb) ...
Preparing to replace linux-headers-generic 2.6.32.21.22 (using .../linux-headers-generic_2.6.32.22.23_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/memtest86+.bin

... has been stuck there for an hour and a half. Any suggestions very welcome. I'm running Lucid on an x86_64 machine.

---

### Post by fishacre on 2010-06-06
Solved - non-problem sorry. Too many windows open so I didn't see it was asking whether I wanted to keep my version of menu.lst....

:oops:

---

