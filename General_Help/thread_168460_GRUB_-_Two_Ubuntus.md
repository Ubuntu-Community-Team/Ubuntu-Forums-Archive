---
title: "GRUB - Two Ubuntus"
date: 2006-04-30
forum: General Help
---

### Post by sprinkles on 2006-04-30
I installed a lot (86) of updates recently, one of which was a kernel upgrade. Now when I see the GRUB menu, there are 2 instances (well, 4 if you include the recovery entries) of Ubuntu, one with the old kernel version, and one with the new one.

How can I get rid of the old kernel version?

---

### Post by Trab on 2006-04-30
u could uninstall it in synaptic, but i dont think thats nessicary...
if u would just like it removed from ur grub menu, do
```
 sudo gedit /boot/grub/menu.lst 
```
and remove the old ones....
cheers
-Trab

---

### Post by Ramses de Norre on 2006-04-30
You can better remove it with apt/synaptic too if you don't use it anymore (though one extra kernel is always handy if the default crashes).

---

