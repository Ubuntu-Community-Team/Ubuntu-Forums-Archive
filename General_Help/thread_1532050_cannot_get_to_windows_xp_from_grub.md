---
title: "cannot get to windows xp from grub"
date: 2010-07-15
forum: General Help
---

### Post by rrsch on 2010-07-15
I downloaded the file boot_info_script&.sh 4 times and it could not be found when i went into terminal mode. 
today i typed in terminal mode: grub update it came back with:
the program 'grub' is currently not installed. you can install it by typing:
sudo apt-get install grup
so i did
sudo apt-get install grub
sudo password for richard
reading package lists . . . done
building dependancy tree
reading state information . . . done
the following packages were automatically installed and are no longer required:
linux-headers-2.6.31-14 linux headers-2.6.31-14 generic
use 'apt-get autoremove' to remove them
suggested packages:
grub-doc mdadm
the following packages will be removed:
grub-pc
the following new packages will be installed:
grub
some character (circle/w dot in middle) upgraded, 1 newly installed, 1 to remove and 54 not upgraded
need to get 903kb of archives.
after this operation 188kb of additional disk space will be used
do you want to continue [y/n] 
i put a n there because i do not know what it is telling/asking me. i thought i had grub on the system?

---

### Post by oldfred on 2010-07-16
There are two boot loaders called grub. Grub legacy (0.97) and grub2 (1.96,1.97 or 1.98). the actual names used to install then are grub for grub legacy and grub-pc for grub2.

If you had grub2 installed and now installed grub you will more than likely have problems. You need to totally remove both and cleanly install one.

You need to find the boot_info_script adn run it so we know what you now have installed. Some systems download to desktop, most now download to Downloads folder.

---

### Post by techunit on 2010-07-16
Well it is safe to say that you just need to type the following into your terminal

```
sudo update-grub
```

---

### Post by rrsch on 2010-07-17
ran sudo update-grub with the folowing results
generating grub.cfg
found linux image: /boot/vmlinux-2.6.31-21-generic
found initrd image: /boot/initrd.img-2.6.31-21-generic
found linux image: /boot/vmlinux-2.6.31-14-generic
found initrd image: /boot/initrd.img-2.6.31-14-generic
found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/my: no such file or directory
found microsoft windows xp professional on /dev/sdb1
done

---

