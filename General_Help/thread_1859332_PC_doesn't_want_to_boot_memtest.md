---
title: "PC doesn't want to boot memtest"
date: 2011-10-13
forum: General Help
---

### Post by biuro74 on 2011-10-13
Hi,

I've got Ubuntu 10.04 x64 on my RAID-0 multiboot machine. The problem appeared once I've changed platform (s775 -> 1155) and I suspect UEFI BIOS as 'guilty'.

On my previous machine everything was working fine, I could launch memtest86+.bin in two ways: through Ubuntu /etc/grub.d/20_memtest+ file (chmod), or "by brute force" and linux 16 directive in my cfg file, leading directly to any memtest file on any partition. This second way worked in GRUB "one" and GRUB2 - which I use now under Ubuntu 10.04, by the way.

But, as I said, I've bought new motherboard & CPU and since then... few things has changed. 
First - booting from CDs/DVDs... it's now kind of different - I've noticed bootpictures disappeared (?!) and many installations start with text screen.
Second - memtest86+ doesn't want to boot anymore.

When I try to initiate boot with "linux" GRUB directive, I've got a message:
error: zImage doesn't support 32-bit boot (try with 'linux16')

.. and with "linux16" GRUB directive (which was fine before) I get now a message:
error: too small lower memory

What can I do ? Does UEFI take too much lower memory ? Have I to report it to mobo manufacturer (I don't think they'd care much about it) ? Or is it any workaround ?

My memtest file is in the newest 4.20 version.

Thanks for any clues

---

