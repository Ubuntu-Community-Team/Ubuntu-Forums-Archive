---
title: "Problem with resume from hibernation"
date: 2011-11-06
forum: General Help
---

### Post by samuelm on 2011-11-06
I am having a problem when resuming from hibernation (suspend to disk) using uswsusp. When I hibernate, everything goes fine, and it shows me that it saves the RAM image into the swap. After it's done, the machine turns off as normal. When I boot up, it displays "Resuming from device /dev/disk/by-uuid/xxxxxxx" with the "throbber" going on for a while. Then, the screen just freezes. I cannot go to any of the ttys or do anything else except reboot with Ctrl+Alt+Delete or turn off with the power button. Any ideas?

My machine specs:

Kubuntu 11.10 x64
AMD Athlon 7550 X2
2.8 GB RAM
6 GB swap (3 GB of swap on a partition that's on a different hard drive than my root partition, and 3GB in a swap file on the root partition)
NVidia graphics card with the NVidia driver from the repos.

---

### Post by LinuxFan999 on 2011-11-06
I have 2 possible solutions:
1. Combine your 2 swap partitions into 1 6GB partition.
2. Don't use hibernation at all.

---

