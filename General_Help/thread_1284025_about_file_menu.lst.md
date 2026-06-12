---
title: "about file menu.lst"
date: 2009-10-06
forum: General Help
---

### Post by linuxwl on 2009-10-06
I Compiled the linux kernel ,then modify the file menu.lst to add a entry to boot the new kernel&#65292;but when I reboot my computer &#65292;I could see the new entry which I have added.
Final I delete the the file  menu.lst ,but  the grub  still have the old entry and  could boot  OS.
I want to know WHY?

---

### Post by ajgreeny on 2009-10-06
If you deleted the /boot/grub/menu.lst there is no way that the machine could boot unless you restored the backup that is made by gedit when you did your file edit, or perhaps you have another linux install from which grub is getting its configuration.

With no menu.lst file there would be a grub error #17 (I think) which would just stop the computer in its tracks.

If necessary, it is possible to rebuild the menu.lst file with info from your system, which will need to be found by running a liveCD.

---

### Post by linuxwl on 2009-10-10
> **ajgreeny said:**
> If you deleted the /boot/grub/menu.lst there is no way that the machine could boot unless you restored the backup that is made by gedit when you did your file edit, or perhaps you have another linux install from which grub is getting its configuration.
 
With no menu.lst file there would be a grub error #17 (I think) which would just stop the computer in its tracks.
 
If necessary, it is possible to rebuild the menu.lst file with info from your system, which will need to be found by running a liveCD.
 
I know the error 17,when delete the menu.lst file,it still can boot,I have search my computer ,could not find  other  boot.
So i fell very surprize and Strange.

---

