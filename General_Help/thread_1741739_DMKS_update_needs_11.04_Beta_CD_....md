---
title: "DMKS update needs 11.04 Beta CD ..."
date: 2011-04-28
forum: General Help
---

### Post by apochry on 2011-04-28
Hi,

one week ago an update named "Dynamic Kernel Module Support Framework" (DMKS) appeared under "Other updates (Ubuntu)" ready for installation. Here is its description:
> DKMS is a framework designed to allow individual kernel modules to be upgraded without changing the whole kernel. It is also very easy to rebuild modules as you upgrade kernels.

When I hit 'Install' the following message shows up:

 [img]http://imgur.com/Xna1w.png[/img] 

I've been ignoring this update for a week, but now I want to upgrade my 10.10 to 11.04 and I'm wondering if it will be needed for proper upgrade, since on the [NattyUpgrades]("https://help.ubuntu.com/community/NattyUpgrades") page they say:
> Be sure that you have all updates applied to your current version of Ubuntu before you upgrade.

... I really don't want to download 11.04 Beta and to burn CDs.

Any Ideas?


Thanks,
Izzo

---

### Post by plucky on 2011-04-28
> 
.. I really don't want to download 11.04 Beta and to burn CDs.

Any Ideas?

Disable the Cdrom as a source in "Software Sources" or it will ask you to load it every time you install or update.

You can get to the "Software Sources" through the Synaptic Package Manager or the Software Centre.

Good Luck

---

### Post by apochry on 2011-04-28
That did the job.
I'm marking this as solved.

Thanks plucky!


Izzo

---

