---
title: "[boot] [grub]"
date: 2010-09-19
forum: General Help
---

### Post by Ma55imo1973 on 2010-09-19
Hi all, I run LL 10.04 since last may without issues. Today I removed an old kernel 2.6.32-22 by uninstalling it from the synaptic package manager, successfully. When updating grub2 with the sudo command, I receive this list of errors:

Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
ERROR: pdc: identifying /dev/sda, magic_0: 0xf413c/0x11ec58, magic_1: 0xf413c/0x0, total_disks: 0
Found Microsoft Windows XP Home Edition on /dev/sda1
done

I could not find any match in my searches, except it is probably something related to the dmraid module. When I run dmraid -s, in fact I find the same error message. Does anyone have any idea about the origin of these error messages ? I used not to see them in the past. Many thanks in advance.

M.

---

