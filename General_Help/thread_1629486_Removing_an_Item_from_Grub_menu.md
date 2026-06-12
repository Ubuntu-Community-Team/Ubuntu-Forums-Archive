---
title: "Removing an Item from Grub menu"
date: 2010-11-23
forum: General Help
---

### Post by ChemMeister on 2010-11-23
Ubuntu updated the Kernel but now i get the two versions (old an new one) in the Grub menu, how do i remove the old version. Thanks,

---

### Post by nl4m on 2010-11-23
It is in "/boot/vmlinuz-2.6.32-24-generic" < Before deleting it, change the name to "...generic.backup", reboot see if it worked. If it did just delete the files. If it did not remove the ".backup".

---

### Post by matt_symes on 2010-11-23
Wrong post. Too many tabs open and getting old.

Actually, after reading your post, i would _really_ suggest keeping at least two kernels. If you get into problems you can boot into the old one.
This has saved me more than once.

Kind regards

---

### Post by lmarmisa on 2010-11-23
I recommend to maintain a couple of versions of kernel in the grub menu.

Anyway, if you wish to remove old versions, uninstall the undesired kernels. Use Synaptic and look for packages named linux-image-2.6...

Be very careful and specially do not remove the newest version of kernel!!!!.

---

### Post by wilee-nilee on 2010-11-23
> **ChemMeister said:**
> Ubuntu updated the Kernel but now i get the two versions (old an new one) in the Grub menu, how do i remove the old version. Thanks,

Generally it is advised to keep at least two kernels sets, one is a back up in case there are problems. The kernel sets take up very little space so you might consider keeping the extra especially if you are a new user or don't know how to compile and insert a set if needed.

---

### Post by jacob.david on 2010-11-23
Which version of grub r u using? you can find it out from the following command
grub-install -v

if it is 1.96 and above you may not edit the /boot/grub/menu.lst directly. It is not allowed. In this case you have to delete the unwanted kernels manually and run the following command.

sudo update-grub.

If the grub version is prior to 1.96 then you can just edit the file /boot/grub/menu.lst and remove the unwanted entry.

---

### Post by matt_symes on 2010-11-23
Hi

> if it is 1.96 and above you may not edit the /boot/grub/menu.lst directly.

Grub2 does not have menu.lst

Kind regards

---

### Post by jacob.david on 2010-11-23
Thanks matt_symes. You are right, it should be grub.cfg and not menu.lst. 
So in grub2 we can't directly edit the grub.cfg.

---

