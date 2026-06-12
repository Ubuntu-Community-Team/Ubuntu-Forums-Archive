---
title: "Please Help! My computer is stuck on a black screen with an error..."
date: 2009-10-23
forum: General Help
---

### Post by TF2-Engi on 2009-10-23
I was uninstalling Ubuntu, in windows I uninstalled the Ubuntu partitions (like this guide said [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)) then I put in the disk to go to repair then fixmbr, then I get a black screen that says:

Grub Version 1.5 Loading(or something like that, the beginning, I wrote down the ending)

Grub Loading, please wait...
Error 22.

Now I have a black screen and my computer can't do anything.  Please help, thank you.

---

### Post by fdrake on 2009-10-23
> **TF2-Engi said:**
> I was uninstalling Ubuntu, in windows I uninstalled the Ubuntu partitions (like this guide said [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)) then I put in the disk to go to repair then fixmbr, then I get a black screen that says:

Grub Version 1.5 Loading(or something like that, the beginning, I wrote down the ending)

Grub Loading, please wait...
Error 22.

Now I have a black screen and my computer can't do anything.  Please help, thank you.
why don't you just make a new install. Probably you have unistalled the prerv partition and the grup is trying to mont a partition that doesn't exist. Don't try to fix it just clean up everything (delete all the partitions) with a fresh install.

---

### Post by TF2-Engi on 2009-10-23
How do I do that?  I have a black screen and it won't go any farther... (Not being sarcastic)

---

### Post by fdrake on 2009-10-23
> **TF2-Engi said:**
> How do I do that?  I have a black screen and it won't go any farther... (Not being sarcastic)
use the live-cd.
1.boot the pc from the cd-rom
2.on the cd screen , select try/boot Ubuntu
3.delete all the partitions using GParted
4.install ubuntu

Are u telling me you cannot boot from the cd?

---

### Post by Lukios on 2009-10-23
Edit: Realized my solution does not apply in this situation.

---

