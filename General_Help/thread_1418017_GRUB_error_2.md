---
title: "GRUB error 2"
date: 2010-02-28
forum: General Help
---

### Post by vkunkel on 2010-02-28
I have read others getting Grub error 2, but i cant fix the problem. I have 2 sata HDDs. I suspect the problem is something to do with RAID?

---

### Post by Axel-P on 2010-02-28
mhmmm, have you checked if the boot up line is correct?

If you have a desktop computer that would probably mean that you linux is installed in (hd0,0) or maybe (hd1,0) you should try to boot from a live CD. I think fstab will tell you where your linux is. Once you got that info, on the grub menu press "e" to edit the line that will boot your linux and edit the line with the new info to be sure you're booting from the right drive. Once you've booted into linux you ca make the change permanent in your menu.lst.

Also, give us the output of "cat /boot/grub/menu.lst" and "sudo fdisk -l" if what I say didn't work.

Ah! and maybe [this]("http://www.gnu.org/software/grub/manual/grub.html") could help you!

---

### Post by vkunkel on 2010-02-28
when I type in "sudo fdisk -l" it comes back as "Unable to seek on /dev/sda"

boot/grub/menu.ist:
title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

---

