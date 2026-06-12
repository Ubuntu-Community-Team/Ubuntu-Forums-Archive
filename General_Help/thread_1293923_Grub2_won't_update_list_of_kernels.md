---
title: "Grub2 won't update list of kernels"
date: 2009-10-17
forum: General Help
---

### Post by ttk1opc on 2009-10-17
I don't know why, but I can not get grub to update the list of kernels, stuck on 2.6.31-11 have to manually edit on boot to get -14, update-grub outputs this...

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Seems like it is working, but nothing changes.

Oh an I am running 9.10 beta

---

### Post by agmcclard on 2009-10-17
I too was having trouble with Grub2 after installing 9.10 2 days ago. I took a chance and did aptitude update aptitude upgrade yesterday and it updated all packages and fixed my grub2 problem. I had manually fixed grub to see my vista os because it would not list it on boot and when upgrading a window popped up asking if I wanted to keep the modified install.  I chose not to keep it and it was reinstalled and upgraded. 

Everything running smoothly and fast. I took a chance since it was so close to the final release and checked to see if their were any upgrades in Synaptic first. I would not upgrade using synaptic though. Aptitude did a great job and held back ubuntu-desktop whereas synaptic wanted to upgrade.  It took a while but I had nothing to lose since it was a clean install of only 2 days ago. Good Luck!

---

