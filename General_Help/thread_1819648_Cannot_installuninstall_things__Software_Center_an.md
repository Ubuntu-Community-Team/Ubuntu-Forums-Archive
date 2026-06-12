---
title: "Cannot install/uninstall things / Software Center and Synaptic won't work."
date: 2011-08-06
forum: General Help
---

### Post by EkViLiBRiUmM on 2011-08-06
Hi! :KS

I'm using Ubuntu Natty, 11.04, with Unity.

There are a couple of problems going on here:

1) First Ubuntu Software Center didn't show anything at all, it kept on loading, forever. I tried to uninstall it and re-install it, as I saw on some other threads, but that just broke it for good. Now I can't even open it. (I have a few guesses on why this could have happened, if you want I can give you a little background story on what I was doing before).
2) If I open terminal and use sudo apt-get update, it gives me this:

> N: Ignoring file 'playonlinux.list.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Type 'enmachines/flash/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/sevenmachines-flash-natty.list
E: The list of sources could not be read.3) If I open Synaptic Package Manager, I get this error:

> E: Type 'enmachines/flash/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/sevenmachines-flash-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

W: Ignoring file 'playonlinux.list.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionI'm not sure what I can do anymore :(

Is there a way to re-install or repair Ubuntu without formatting the partitions?

This is my first time with Ubuntu (and Linux at all), I've been using it for one week now.
Thank you in advance, this community and this forum are great! ^^

---

### Post by xdominex on 2011-08-06
Open nautilus as root by pressing Alt+F2 and typing "gksudo nautilus". Once in nautilus, navigate to /etc/apt/sources.list.d/ and delete your "sevenmachines" files from this directory. If necessary, also delete the playonlinux files from the same directory. After doing so, try running "apt-get update" again and see how it goes. Report back after trying. Hope this helps!

---

### Post by EkViLiBRiUmM on 2011-08-07
Hey! thanks a lot! Unfortunately, I was in a hurry so I just did a re-install of Ubuntu.

---

### Post by Basher101 on 2011-08-07
please mark your thread as [SOLVED] if your problem got fixed

---

