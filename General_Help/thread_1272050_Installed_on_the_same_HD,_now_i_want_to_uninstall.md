---
title: "Installed on the same HD, now i want to uninstall"
date: 2009-09-21
forum: General Help
---

### Post by tmos22 on 2009-09-21
Hi , i installed ubuntu on the same harddrive as xp earlier but now i want to uninstall it, how do i do this?

---

### Post by Jimmynemo2 on 2009-09-21
Did you install on a seperate partition or by using WUBI?

---

### Post by tmos22 on 2009-09-21
I chose at the start to run it on the same drive as xp. I installed it on my laptop with no problems. This is on my desktop. I only have one drive so it must be on that. Im confused. Next time i'm just going to create a partiton

---

### Post by rapt0rjezuz on 2009-09-21
> **tmos22 said:**
> I chose at the start to run it on the same drive as xp. I installed it on my laptop with no problems. This is on my desktop. I only have one drive so it must be on that. Im confused. Next time i'm just going to create a partiton

EDIT: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)      This link goes into detail how you could remove Ubuntu without removing any of your Windows files.


I'm guessing you chose the "Install inside windows" option?

Try searching the forums for a similar thread about your problem, heres one for starters:

[http://ubuntuforums.org/showthread.php?t=856140](http://ubuntuforums.org/showthread.php?t=856140)

Wish I could be of more help.

---

### Post by Jimmynemo2 on 2009-09-21
Ok, so just to verify, you can open a terminal, and type:

Sudo apt-get install gparted

once it is installed, open it up, and you can see if you already have multiple partitions. (be careful not to try anything odd here, as you could biff your XP install too)

1- if you DO NOT have more than one partition, then you likely installed using whats called WUBI- so boot back into XP, open your add/remove programs page, and see if ubuntu is listed to uninstall from there.

2- IF YOU DO have more than one parition, you installed ubuntu on a seperate partition, and can anyone give good instructions, as I've always just reloaded XP in this senario? (I know it involves replacing grub with XP's bootloader and then deleting the ubuntu partitions, but I save time and reload)

---

