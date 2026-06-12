---
title: "Dual boot and Kernel upgrades"
date: 2009-11-26
forum: General Help
---

### Post by GodLikeCreature on 2009-11-26
Hi all,

I have been using partitions for a long time, because I like booting to different flavors of Linux, sometimes even different versions of Ubuntu.  For example, I have a PC with a Jaunty installation that I put together 6 months ago, and then I installed Karmic on another partition.

Therefore, I get a dual boot menu to choose between them at startup.  However, when I get Kernel upgrades, the last upgrade is updated fine in the Grub menu for Karmic, but not for Jaunty.

Let me try to give an example, just to clarify.  Grub menu shows something like this:

Ubuntu v2
Ubuntu v1

(simplified to depict the situation.  Ubuntu v2 = Karmic, Ubuntu v1 = Jaunty)

When I get a kernel upgrade, the menu would automatically show the following:

Ubuntu v3 (Ubuntu v2 + kernel upgrade)
Ubuntu v2 (old entries remain in /boot/grub/menu.lst)
Ubuntu v1 HERE is the problem.  

Even if I get a kernel upgrade on Jaunty, it does not get updated on this menu.  I suspect this is down to the file menu.lst file being on the Karmic partition.

If I am right, then it cannot be done automatically, but can I do it manually?  I have checked the entries on menu.lst, and I could manually fix one for the new Jaunty kernel.  The only catch is that I don´t know what its uid is.  

How can I get all the info for a new kernel entry?
Would such manual entry work?

Thanks!

---

### Post by GodLikeCreature on 2009-11-26
Any ideas anyone?

---

