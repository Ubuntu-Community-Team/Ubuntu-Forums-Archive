---
title: "Using GRUB as replacement boot-loader"
date: 2011-06-04
forum: General Help
---

### Post by DuxWonder on 2011-06-04
Hello all, 

Well, I've experimented a bit with Ubuntu on my laptop, ( Quite an older model, Dell C840) and have found that Unity will not work with the computer's video card. (GNOME is also too heavy to be effective) I would like to remove my linux partition, but have found that I have misplaced my Windows XP boot disc. (oops!) Is it possible to install GRUB as the replacement boot-loader with Windows as the sole operating system?

(I'll probably try a more lightweight OS such as Xubuntu later, but for now I just want to remove Ubuntu)

Thanks,
-DuxWonder

---

### Post by garvinrick4 on 2011-06-04
You can boot XP with Lilo:
With a Ubuntu install Cd using Try Ubuntu with internet working:
Install Windows bootloader with Linux Live CD: 

#Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot:
Should boot into Windows:
Then you can delete Linux partition and resize Windows if you choose:

---

### Post by DuxWonder on 2011-06-25
Worked like a charm. Many thanks to you, sir.

---

