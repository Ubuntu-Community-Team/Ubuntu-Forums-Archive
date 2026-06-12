---
title: "Grub2 CLI Mode"
date: 2011-04-15
forum: General Help
---

### Post by Zelda Hunter on 2011-04-15
I once again had to reinstall Windows 7. Both Ubuntu 10.10 and Windows 7 were loaded, but I could only boot into Windows 7; and for some reason a Live USB wasn't booting anymore.

Basically, I messed around and got to boot in Ubuntu. Unfortunately, Grub is now in Command Line Mode and won't change back into the normal bootlaoder. I can only boot to Ubuntu using the following lines:

linux (hd0,1)/vmlinuz root=/dev/sda1
initrd (hd0,1)/initrd.img
boot

I've been at this problem for a few hours, so can someone be kind and tell me how to fix Grub back into a bootloader that can boot Ubuntu and Win7?

---

### Post by idoitprone on 2011-04-15
I am confused. Is grub still in the mbr?

If so, then boot to ubuntu and 

```
sudo update-grub
```

If grub is not in the mbr, you will have to reinstall grub. This link should tell you everything you need to know?



Just read the first paragraph, this might explain the situation, I guess
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2)


looking at other problem that you are not telling about
[https://help.ubuntu.com/community/Grub2#Post-Restoration](https://help.ubuntu.com/community/Grub2#Post-Restoration)

---

### Post by wilee-nilee on 2011-04-15
If you can get into ubuntu in the terminal run
sudo grub-install /dev/sda
then 
sudo update grub

grub will then be in the mbr

If you're running burg sub burg for grub.

---

### Post by Zelda Hunter on 2011-04-15
I believe wilee-nilee's commands worked. I can finally boot both OSs. If I could, I'd delete Windows 7, but other people use it.

Thanks for the help! :P

---

