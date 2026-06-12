---
title: "Restoring Ubuntu GRUB?"
date: 2012-04-06
forum: General Help
---

### Post by joemartin on 2012-04-06
Dual booting Precise with PCLOS.  

I want to use G-Parted to eliminate PCLOS partition and grow Ubuntu's to 100%.  

The problem is I installed Ubuntu with GRUB but at boot it defaults to PCLOS's GRUB menu and not Ubuntu's.  

How can I make sure that Ubuntu's GRUB will load after I delete PCLOS and have it automatically load Ubuntu?  Don't want to have a borked boot after deleting PCLOS.

Thanks.

---

### Post by Quackers on 2012-04-06
You can boot into your Ubuntu system then run the command below in the terminal. Please Note that this installs (Ubuntu's) grub to the MBR of the drive and therefore will be in control. 
The /dev/sda used in the command refers to the hard drive your bios boots from. You will need to change that if you don't boot from /dev/sda
```
sudo grub-install /dev/sda
```
Once grub is installed you can run ```
sudo update-grub
``` which should then reveal any other OSes installed (or delete any other OSes' partitions, if you wish).

---

