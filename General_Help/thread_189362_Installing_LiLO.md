---
title: "Installing LiLO"
date: 2006-06-05
forum: General Help
---

### Post by GooOS on 2006-06-05
hello
how can i install Lilo ? using The KUBUNTU LIVEcd..

---

### Post by localzuk on 2006-06-05
Hi,

First can I ask a few questions?

1. Install it to where?
2. Why lilo and not grub?

---

### Post by GooOS on 2006-06-05
let me tell you a story:
I reinstalled windows (you can guess why) so grub was eaten by the Microsoft boot, i tried to reinsatll it by:
```
grub> root (hd1,0)
grub> setup(hd1)

```

but instead of getting a boot loader i got a continuious loop of 
```
Grub stage 1.5
```
so i will try to install lilo to get  a working bootloader

---

### Post by localzuk on 2006-06-05
Take a look at [http://www.shahidhussain.com/wordpress/index.php?p=33](http://www.shahidhussain.com/wordpress/index.php?p=33) for information on reinstalling grub.

---

### Post by GooOS on 2006-06-05
The problem is I can't mount /dev/hdc1 because it does not exist in the /dev folder but QTparted detects it (as /dev/hdc1 so when I try to install GRUB it says that it can't find the menu.lst file1
```
grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+15 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub>                                 
```
what can i do?

---

### Post by GooOS on 2006-06-05
Fixed it!

It seems to be that the IDE Cable is damaged!
replaced it and everything works fine...

thank you for your efforts

---

