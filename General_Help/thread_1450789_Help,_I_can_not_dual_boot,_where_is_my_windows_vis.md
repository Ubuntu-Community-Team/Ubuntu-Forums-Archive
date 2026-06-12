---
title: "Help, I can not dual boot, where is my windows vista gone?"
date: 2010-04-09
forum: General Help
---

### Post by lucky6877 on 2010-04-09
Guys,

Just installed 9.10 on my home computer which already had windows vista running, I allocated a spare partition and install ubuntu on it, I was expecting to see windows vista optnio after reboot but I only get 5 options from the menu, where is my windows vista gone?

Here is my list from /boot/grub/menu.lst:

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/mapper/isw_bghhihchbh_ARRAY6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/mapper/isw_bghhihchbh_ARRAY6 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_bghhihchbh_ARRAY6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_bghhihchbh_ARRAY6 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin



Please help me.

---

### Post by dannyboy79 on 2010-04-09
it appears as though grub didn't pick up your windows install. did you install grub to the mbr or to a partition? can you show me an ouptut from this command:
sudo fdisk -l
that will show me all your harddirves and partitioning scheme on each drive. also, please inform me where ubuntu is and where you think vista is. you could tell by the size of teh partition. it most likely didn't erase windows vista unless of course you used the installer and told it to use the entire disk and auto-partitio it, then it woiuld've deleted everythign from the drive and created new partitions for root and swap i beleive. good luck

---

### Post by Mark Phelps on 2010-04-10
Boot into Ubuntu, open a terminal, and enter "sudo update-grub" and watch as it searches for kernels and OSs.  You should see it find a line like Windows Vista loader found on (sda1)".

When you reboot, you should have a menu entry for Vista.

---

### Post by oldfred on 2010-04-10
Grub2 is real good at finding windows, grub legacy was ok at finding it. You are showing menu.lst which is grub legacy. I remember helping a lot of users with windows entries in old grub, but not with raid.

You also have some sort of raid? /dev/mapper/isw_bghhihchbh_ARRAY6
I do not know raid but have seen several posters have trouble getting Ubuntu/grub to work with raid unless it was a server install.

If the update does not work post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

