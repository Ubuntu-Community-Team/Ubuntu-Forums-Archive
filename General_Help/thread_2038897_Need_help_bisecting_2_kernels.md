---
title: "Need help bisecting 2 kernels"
date: 2012-08-07
forum: General Help
---

### Post by rihad on 2012-08-07
Hi, folks. I've been experiencing a Kubuntu bootup issue of kernel not initializing Device Mapper properly (see [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/880646) for details). Now I need to bisect 2 kernel versions to determine which commit started triggering this bug, and since I'm in no way a kernel dev I'm having a hard time with that. Can you write or point me to a simple how-to on the matter? I've tried [this one](https://wiki.ubuntu.com/Kernel/KernelBisection), but I just can't get it right.
Specifically I need to bisect these kernel versions:
good: 2.6.37-11.25
bad: 2.6.37-12.26

"bad" is where things started being wrong.

TIA!

---

