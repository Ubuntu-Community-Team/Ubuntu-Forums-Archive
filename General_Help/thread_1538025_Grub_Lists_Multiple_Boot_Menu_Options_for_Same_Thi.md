---
title: "Grub Lists Multiple Boot Menu Options for Same Thing"
date: 2010-07-24
forum: General Help
---

### Post by jereece on 2010-07-24
I did a fresh install of Ubuntu 10.4 a couple weeks ago and have always wondered why Grub list multiple boot options in the boot menu for the same thing.  For example, mine lists the main Ubuntu boot, a Ubuntu recovery mode boot and a Windows boot.  However the main Ubuntu boot and Ubuntu recovery boot are listed a total of 3 times. Are the duplicates for some particular reason?  If not how can I clean up the Grub boot menu?

Thanks,
Jim

---

### Post by munkyeetr on 2010-07-24
Most likely each entry pair (Ubuntu and Ubuntu Recovery) load different kernels.

Post the contents of your **/boot/grub/grub.cfg** file.

---

### Post by howefield on 2010-07-24
Every time there is a kernel update in your update list, you'll get new entries in the boot loader.

It can be useful to keep at least the latest and next to latest, the others can be removed using Synaptic Package Maanger if you wanted to, although they won't be doing any harm other than taking a small amount of space.

---

### Post by Rubi1200 on 2010-07-24
> **jereece said:**
> I did a fresh install of Ubuntu 10.4 a couple weeks ago and have always wondered why Grub list multiple boot options in the boot menu for the same thing.  For example, mine lists the main Ubuntu boot, a Ubuntu recovery mode boot and a Windows boot.  However the main Ubuntu boot and Ubuntu recovery boot are listed a total of 3 times. Are the duplicates for some particular reason?  If not how can I clean up the Grub boot menu?

Thanks,
Jim
The additional GRUB entries are probably different kernels. I assume you had kernel updates since you first installed?

You can remove them using Synaptic; search for linux image and linux headers, removing the versions you don't want.

Just make sure you don't remove the most recent version!

By the way, some people like to keep at least one previous kernel version as a sort of safety net.

---

