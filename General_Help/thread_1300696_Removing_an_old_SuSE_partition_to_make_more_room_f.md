---
title: "Removing an old SuSE partition to make more room for Xubuntu"
date: 2009-10-25
forum: General Help
---

### Post by jongudm on 2009-10-25
I am running a triple boot setup on my laptop at the moment, with WinXP (preinstalled), Xubuntu 9.04 and SuSE all functioning perfectly.  I've copied all data from the SuSE partition to a safe place and I'm wondering how best to go about removing that partition and giving Xubuntu the space it was using.  Is it safe to use the partition utility on the live CD to simply let the Xubuntu partition "eat" the SuSE one (in other words to delete it and then grow the Xubuntu partition into the available space) or will that damage something?  Is there some other better way to do this?

---

### Post by Aero-Z on 2009-10-25
> **jongudm said:**
> I am running a triple boot setup on my laptop at the moment, with WinXP (preinstalled), Xubuntu 9.04 and SuSE all functioning perfectly.  I've copied all data from the SuSE partition to a safe place and I'm wondering how best to go about removing that partition and giving Xubuntu the space it was using.  Is it safe to use the partition utility on the live CD to simply let the Xubuntu partition "eat" the SuSE one (in other words to delete it and then grow the Xubuntu partition into the available space) or will that damage something?  Is there some other better way to do this?
Install gparted or boot with live-cd. You can play around with your partitions with it. Try make sure that you delete the right partition(s).

---

### Post by jongudm on 2009-10-25
Thanks for the reply.  What I'm wondering though is if just deleting the partition will mess things up for the boot loader, when all of a sudden one of the operating systems it has listed isn't there anymore?

---

