---
title: "Remove old entries from 2nd HD in boot menu"
date: 2010-07-29
forum: General Help
---

### Post by Oldhacker on 2010-07-29
Running 10.04 64 bit, I have a few entries in the Boot menu left over from previous versions of Ubuntu and Suse. Removing entries using Synaptic Package Manager is simple. However, these old items booted from my 2nd HD, and they do not show up in Synaptic
(but they clutter up the present Boot menu.)

How can I get rid of them?

Thanks

---

### Post by chopinhauer on 2010-07-29
> **Oldhacker said:**
> 
How can I get rid of them?


```
sudo update-grub
```
on the system that manages the computer login should do it.

---

### Post by oldfred on 2010-07-30
If you want it to stop finding other systems, you can turn off osprober.

In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

But if the prober is finding other systems you want, you need to first copy those boot stanzas from grub.cfg to 40_custom. If you add another system you can temporarily turn prober back on.

---

### Post by Oldhacker on 2010-07-30
Actually, disabling access to other systems is not what I had in mind. I would prefer to just delete the couple of obsolete distributions (the SUSE's and the old Ubuntu on the 2nd HD) and have the space available for experimenting with other newer distros. I am still not sure how to accomplish this.

---

### Post by oldfred on 2010-07-30
If you have backed up any data you want, use gparted and reformat the partitions. Then there will be nothing there for osprober to find. If the partitions are not mounted you can use synaptic to download gparted in Ubuntu (its not normally installed as you cannot work on mounted partitions). Otherwise use a liveCD.

---

