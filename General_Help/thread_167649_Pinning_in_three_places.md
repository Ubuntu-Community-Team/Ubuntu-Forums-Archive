---
title: "Pinning in three places"
date: 2006-04-28
forum: General Help
---

### Post by Andrew-buntu on 2006-04-28
I compiled wine from source by using apt-get --build source to make a .deb (needed to patch for WoW).  I'd like to stop updating it until the next version.  So I made an /etc/apt/preferences file and created a pin entry for it.  It seems to work and if I use apt-get upgrade, wine is listed as "held back".  Great!
But if I update through synaptic, it tries to update wine - this despite me ALSO pinning the package in synaptic (pinning in /etc/apt/preferences doesn't seem to effect synaptic).  I think synaptic isn't happy with my local version and wants to reinstall from the WINE HQ repository.
Finally, the update manager icon in my panel bugs me every time I log on about having one package to update - wine, of course.
Is there a way to pin packages in all places?  I thought the gui frontends acted upon apt so pinning once would do it all.

---

