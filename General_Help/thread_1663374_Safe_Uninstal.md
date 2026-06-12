---
title: "Safe Uninstal"
date: 2011-01-09
forum: General Help
---

### Post by Sanchenzo on 2011-01-09
I was wondering if there was a safe way to uninstal Ubuntu without having to screw up the GRUB?
 
This is not the first time I have uninstalled Ubuntu for modifications and everytime it has screwed up the GRUB in the proccess, and then having to repair the boot with my Windows 7 CD. Is there a safe way to remove Ubuntu?

---

### Post by Sanchenzo on 2011-01-09
This is just temporary to make some adjustments for Ubuntu

---

### Post by CharlesA on 2011-01-09
What do you mean by adjustments?

---

### Post by Sanchenzo on 2011-01-09
The amount of memory I'm putting into Ubuntu

---

### Post by CharlesA on 2011-01-09
Is this a Wubi install, or what?

If you are resizing the partition be sure to back up your data and then resize it.

Shouldn't have to mess with Grub.

---

### Post by hhh on 2011-01-09
I take it you want to keep Grub because you have another Linux OS installed on that computer? Boot into that other Linux OS and run this command in a terminal...```
sudo grub-setup /dev/xxx
``` where "xxx" is the name of the entire drive, not just the partition, where the OS is installed. So on my system, I run...```
sudo grub-setup /dev/sda
``` An easy way to see the drive path is to open Gparted, it should be in the drop-down menu in the upper-right corner.

When that's done, run ```
sudo update-grub
``` and reboot to verify that the other OS is at the top of the Grub menu. If it is, go ahead and remove Ubuntu without worries.

---

### Post by mike555 on 2011-01-09
What kind of install is it ? virtualbox ?  otherwise if it's a real install ,just install over the old one.

---

