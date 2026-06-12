---
title: "cupsd doesn't start"
date: 2011-03-22
forum: General Help
---

### Post by klausner on 2011-03-22
*cupsd* has ceased starting at boot time. It is checked off in System->Administration->BootUp Manager, and it runs fine from the command line. But not at boot.

This is **not** the problem reported [here]("http://ubuntuforums.org/showthread.php?t=1416651").

I suspect there are a couple more processes that have stopped running, but their absence hasn't been obvious yet.

FWIW, I'm running 10.04 with the 2.6.35-22 kernel.

---

### Post by cavalier911 on 2011-03-23
See these bug reports:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172?comments=all)

---

### Post by klausner on 2011-03-23
> **cavalier911 said:**
> See these bug reports:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172?comments=all)

Thanks for the links. The first doesn't seem to match, but the second is definitely about *cupsd* start problems. Unfortunately, there is so much arguing going on about other issues too, it's hard to dig out answers. I'm going to try a couple of the things they suggest, and see if they help.

---

