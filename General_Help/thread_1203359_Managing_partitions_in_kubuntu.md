---
title: "Managing partitions in kubuntu"
date: 2009-07-03
forum: General Help
---

### Post by John M2009 on 2009-07-03
I installed kubuntu a while ago with the intention of having a dual boot configuration,  but now I have no intention of using windows ever again,  so I have a partition sitting around doing nothing and it seems a shame to waste it.  I was wondering if there was a way to edit/manage partitions from the kubuntu desktop and make it my /home directory. The only other alternative i have is to do a clean reinstall using the whole disk,  something I really dont want to have to do,  considering the amount of trouble I had getting everything to work the first time round.

---

### Post by starcraft.man on 2009-07-03
You can use GParted either from the liveCD (you might have to install it from the repositories). The other way would be to download a [live GParted]("http://gparted.sourceforge.net/download.php") CD and burn it. If you want help using gparted, see their documentation section.

Anyway, once you have gparted, just delete the Windows partition and either make a new one with the FS of your choice or merge the space into another one. See documentation if your unsure.

Backup all vital data before doing this operation. You never know what can happen, even though it usually doesn't.

---

