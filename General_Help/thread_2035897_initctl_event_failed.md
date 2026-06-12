---
title: "initctl event failed"
date: 2012-07-31
forum: General Help
---

### Post by wesyde on 2012-07-31
I've been running an intranet server on this machine for the past month or so and it as working great.  Then the server stopped displaying pages, so I ended up trying to restart the machine. Now when I attempt a normal boot, I get blank screen and nothing else.  

Booting in recovery mode and selecting "resume"  Gives me the following result:

```
Ubuntu 12.04 LTS praxis1 tty1

praxis1 login: initctl: Event failed
```

Selecting "dpkg", "fsck", or "grub" gets me to a screen which gets to the following and then hangs:

```
fsck from util-linux 2.20.1
/dev/sda5: Superblock last mount time is in the future.
 (by less than a day, probably due to the hardware clock being incorrectly set) FIXED.
/dev/sda5: clean, 97465/101088 files, 388700/403712 blocks
```

The date and time seems to be set correctly.

Selecting the root boot option is not an option for me since I never set a root password.

I'm not sure where to proceed from here.

---

