---
title: "[Grub] persistent append of options to kernel boot line"
date: 2009-12-08
forum: General Help
---

### Post by takai on 2009-12-08
Ok, have a simple little issue with Grub, where on some of our laptops we need to append a bunch of options (i8042.reset etc) as per: [http://patchwork.kernel.org/patch/62455/](http://patchwork.kernel.org/patch/62455/)

However, whenever we update the kernel or grub it hoses all of the options in menu.lst

Is there any way of getting it to persist throughout the grub-update?

---

### Post by ranch hand on 2009-12-08
Since you have a menu.list you have to be using grub-legacy.

You are going to have to edit the menu.lst.

This is one of the reasons that those commands are moved to /etc/default/grub in grub2.

You might want to try grub2.  I would research it a lttle as it is completely different.  The link in my sig is a good place to start.  The first 3 links that I provide are about as good as any in depth info you will find.

You must consider that grub0.97 (grub-legacy is not supported by the grub project any more.

If you are using Jaunty, grub version 1.96 is in the repo.  What we are using in karmic and Lucid-testing is grub1.97beta4.  If all you have is one drive and just ubuntu or ubuntu and some MS version, you should have no trouble at all.

You put those instructions in /etc/default/grub and use the symbolic menu entry in a custom file and you will never have to worry about updating at all as it will boot to the newest kernel on the partition.

---

