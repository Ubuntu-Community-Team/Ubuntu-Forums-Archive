---
title: "update grub error"
date: 2012-01-11
forum: General Help
---

### Post by warto on 2012-01-11
windows 7 not shown in my grub menu. then resolve it with reinstall grub. but, when update grub shown error as:

warto@warto-Compaq-510:~$ sudo update-grub
Generating grub.cfg ...
Found background image: /usr/share/images/grub/sabily.png
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/01CC31A96D0F3910/boot                     <-- error here
Boot: No such file or directory
done

how to fix it?

---

### Post by raja.genupula on 2012-01-11
do this 
sudo dpkg-recnfigure grub-pc

 place grub choice to  sda and then give me the output what you have got .

---

### Post by warto on 2012-01-11
> **raja.genupula said:**
> do this 
sudo dpkg-recnfigure grub-pc

 place grub choice to  sda and then give me the output what you have got .

**[B][RESOLVED]**[/B]
i try your soution, but there were not solving my problem. then i tryed this solution at local Indonesian ubuntu forum: [http://www.kaskus.us/showthread.php?p=550961141](http://www.kaskus.us/showthread.php?p=550961141)

to fix my problem, i try BOOT-REPAIR from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

but in this case, thanks for u'r attention and suggestion.
:popcorn:

---

