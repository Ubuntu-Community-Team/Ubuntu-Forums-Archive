---
title: "Compiled kernel, sound not working"
date: 2009-09-02
forum: General Help
---

### Post by Cato2 on 2009-09-02
I compiled a Hardy 2.6.24 kernel using this howto - [https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way) - this worked well and I managed to get HIGHMEM64G enabled (PAE kernel with full 4GB RAM used), which is good.  I downloaded the linux-source package using "apt-get install linux-source" and the resulting directory is linux-2.6.24.2.  

However, despite basing the kernel config on the /boot/config.xxx file used by the running -generic kernel, some features don't work, e.g. ALSA sound using an in-tree driver module (HDA Intel) - the alsa and snd drivers don't load, probably because they aren't in the tree /lib/modules/2.6.24.6-20090830-pae.

The latest kernel installed by apt-get was 2.6.24-24-generic - this doesn't correspond at all to the version number of the tree downloaded by the linux-source package (2.6.24.2).  So, how can I download the exact Ubuntu-patched source for 2.6.24-24-generic and use this as a base?

I have also started to try the other technique on that page (starting at [https://help.ubuntu.com/community/Kernel/Compile#Get%20the%20kernel%20source](https://help.ubuntu.com/community/Kernel/Compile#Get%20the%20kernel%20source) and doing apt-get source to get the tree). This results in the following two files, which seem to match the version I want:

-rw-r--r--  1 richard richard  4772536 2009-08-19 06:06 linux_2.6.24-24.59.diff.gz
-rw-r--r--  1 richard richard     2257 2009-08-19 06:06 linux_2.6.24-24.59.dsc

Can someone confirm which technique I should be using to rebuild 2.6.24-24-generic?  I feel like I'm really close...

---

### Post by Cato2 on 2009-09-04
The solution to this was to re-run "make xconfig" and ensure that ALSA (Advanced Linux Sound Architecture) was selected (and all its sub-options, as modules), and re-build the kernel.  Seems that ALSA modules are not included in the default kernel config, perhaps because the alsa-base package includes these.

Sound is now working fine with a 32-bit PAE kernel.

---

