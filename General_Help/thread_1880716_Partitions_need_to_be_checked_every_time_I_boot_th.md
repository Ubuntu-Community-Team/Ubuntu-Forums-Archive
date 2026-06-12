---
title: "Partitions need to be checked every time I boot the PC"
date: 2011-11-14
forum: General Help
---

### Post by dv_ on 2011-11-14
Hi, I am experiencing something odd. Every time I boot, fsck comes up and has to replay the boot partition's journal.

Additionally, I have a second data partition. This one should get automounted at startup, but isn't, because it too needs to be checked with fsck.

Now this happens every single time I (re)boot. It is as if Ubuntu is not unmounting the partitions cleanly.

I already tried to fsck from a live CD. After that, the system started correctly, but afterwards, after a reboot, the problem came back again.

So, what is going on? I am using Ubuntu 11.04 .

---

### Post by dcstar on 2011-11-14
> **dv_ said:**
> Hi, I am experiencing something odd. Every time I boot, fsck comes up and has to replay the boot partition's journal.

Additionally, I have a second data partition. This one should get automounted at startup, but isn't, because it too needs to be checked with fsck.

Now this happens every single time I (re)boot. It is as if Ubuntu is not unmounting the partitions cleanly.

I already tried to fsck from a live CD. After that, the system started correctly, but afterwards, after a reboot, the problem came back again.

So, what is going on? I am using Ubuntu 11.04 .

Have you recently installed/upgraded VMware Workstation/Player?

---

### Post by dv_ on 2011-11-14
> **dcstar said:**
> Have you recently installed/upgraded VMware Workstation/Player?

Indeed I have, why?

---

### Post by dv_ on 2011-11-17
Again: why? I cannot find anything about VMware and Ubuntu causing filesystem errors in cases where Ubuntu is the host.

---

### Post by dcstar on 2011-11-18
> **dv_ said:**
> Indeed I have, why?

Because there is a bug in VMware Player that wrecks your system's startup & shutdown file orders and causes unclean filesystems which result in slow startups.

Look in the Virtualization forum for my thread on this.

---

