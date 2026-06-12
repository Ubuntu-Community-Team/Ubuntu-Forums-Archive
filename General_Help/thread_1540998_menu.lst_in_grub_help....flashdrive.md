---
title: "menu.lst in grub help....flashdrive"
date: 2010-07-28
forum: General Help
---

### Post by rtllz on 2010-07-28
hi, i had a quiestion about my ubuntu menu.  I tried to move its location in my flashdrive to a different location and i edited my menu accordingly but it didnt want to boot anymore.  Im thinking its because i didnt change the line in on the kernel that says "boot=casper".  Any help would be appreciated

title Ubuntu LiveCD 10.04
find --set-root /ubuntu10.04.iso
map /ubuntu10.04.iso (0xff) Grubl2
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu10.04.iso quiet splash --
initrd /casper/initrd.lz
boot find /home

---

