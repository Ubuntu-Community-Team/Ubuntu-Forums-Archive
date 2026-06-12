---
title: "Randomly moving icons"
date: 2009-09-03
forum: General Help
---

### Post by Warthaug on 2009-09-03
I have run into what seems to be a simple problem, but one I cannot seem to find an answer to.

Every time I use my ubuntu-running laptop with a projector, the next time I log on many of the icons on the top bar - volume, power, wireless, power, lock-screen, date/time, are moved around out of the original order.

Some of them I can move back, but the battery status icon and wireless network icon seem to be unmovable - I cannot find a "lock to pannel" option to de-check, and the usual trick of "grabbing" the icons with both mouse buttons simply opens up the dop-down dialougs for the icons.

How do I put them back, and is there any way of keeping them from moving in the first place?

Bryan

---

### Post by tgeer43 on 2009-09-03
Usually when the panel icons get moved around like that it's due to a resolution change that's not done quite properly. That may be what's happening when you connect the projector.

The only workaround that I've found is to manually change to the projector's desired resolution before connecting it then changing back when you are done. This will at least keeps your panel icons from moving around.

tgeer

---

### Post by lazlo on 2011-05-30
Hi all,

even though this is a quiet old post I have a kind of workaround for the "randomly moved panel icons" problem.

I run "gconftool-2 --dump /apps/panel > panel-settings-backup.xml" once when everything is fine.

When things are messed up i run "gconftool-2 --load panel-settings-backup.xml", then log out and in again - then panel icons are back where they should be.

Still this is no real solution (and the problem is still there with Ubuntu 10.10).

---

