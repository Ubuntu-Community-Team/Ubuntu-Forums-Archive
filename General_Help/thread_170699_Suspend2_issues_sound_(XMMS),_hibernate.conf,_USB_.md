---
title: "Suspend2 issues sound (XMMS), hibernate.conf, USB drive"
date: 2006-05-05
forum: General Help
---

### Post by geek.de.nz on 2006-05-05
Hi,

I followed the guide "**HOWTO get Hibernate working with Proprietory Nvidia driver (using Suspend2)**" and have a couple of problems:

[LIST=1]
[*]Sound: When I play music in XMMS or play any sort of sound and hit the power button to suspend2 disk, the next time I boot up my sound doesn't work anymore, i.e. when I press play in XMMS it comes up with an error message. When I try to reload alsa, nothing happens. Sound would still not work until I reboot. This doesn't happen if I stopped playback though.
[*]/etc/hibernate/hibernate.conf: The options OnSuspend NN <program> and OnResume NN <program> don't seem to work for me. I tried to fix the sound problem, simply by remote controlling XMMS to stop playback, but that doesn't work either. It seems as though the option doesn't exist.
[*]USB drive: My external USB Hard Drive sometimes stops working when I boot the suspend2 kernel (or better becomes /dev/sdb instead of /dev/sda). This seems to happen randomly. Also, I get annoying error messages from konqueror, telling me that the drive could not be mounted when I resume from hibernation.[/LIST]   Any ideas? Help would be greatly appreciated. Thanks.

---

