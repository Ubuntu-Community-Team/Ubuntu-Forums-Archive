---
title: "Problem with dual boot"
date: 2012-06-23
forum: General Help
---

### Post by tears of the river on 2012-06-23
I dual booted ubuntu 12.04 with freeBSD and i configured grub 2 in order to show the freeBSD option upon boot up however now i want to uninstall freeBSD and dual boot ubuntu 12.04 with backtrack 5.

I uninstalled freeBSD by reformatting the partition through gparted however when i rebooted there was some sort of error as it did not detect the os in the system. however as soon as i reinstalled freeBSD the computor started working again. i think this has to do with grub 2 although im not the expert.

Could someone please help as 100GB is being wasted in freeBSD space that i barely ever use

Thanks in advance

---

### Post by Redblade20XX on 2012-06-23
Do you have grub2 installed in Ubuntu or FreeBSD? The location of the bootloader is essential because it will direct the boot process to the distro with the stated files. So if the files in grub2 point to the FreeBSD partition and you nuked the partition you'll get an error.

If this is the case and you have FreeBSD still installed, just boot into the Ubuntu partition and reinstall grub2 in it.

Another fix is to create a Ubuntu live cd, boot into a live session and use boot-repair to get grub2 to point to the Ubuntu partition.

-Red

---

### Post by tears of the river on 2012-06-24
> **Redblade20XX said:**
> Do you have grub2 installed in Ubuntu or FreeBSD? The location of the bootloader is essential because it will direct the boot process to the distro with the stated files. So if the files in grub2 point to the FreeBSD partition and you nuked the partition you'll get an error.

If this is the case and you have FreeBSD still installed, just boot into the Ubuntu partition and reinstall grub2 in it.

Another fix is to create a Ubuntu live cd, boot into a live session and use boot-repair to get grub2 to point to the Ubuntu partition.

-Red

I think that i did the grub in Ubuntu as i ran a code of grub update or something like that in ubuntu's terminal

---

