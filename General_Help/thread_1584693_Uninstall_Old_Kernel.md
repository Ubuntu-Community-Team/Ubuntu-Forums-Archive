---
title: "Uninstall Old Kernel"
date: 2010-09-29
forum: General Help
---

### Post by madzombie on 2010-09-29
Hi,
i update kernel  2.6.32-24 to 2.6.32.25.
But i want to uninstall old kernel version. 
How can i do the operasion ?

Thanks.

---

### Post by TeoBigusGeekus on 2010-09-29
It's a good idea to keep the last 2 kernels on your system. This way, if something goes bad with the latest, you can always switch to the previous one.
If you insist, or when the kernels begin to pile up, open synaptic package manager, search for linux-image and completely remove the older ones.

---

### Post by efflandt on 2010-09-29
Actually if you want to get rid of everything related to old kernels you can put **linux** in Quick search of Synaptic and look for any packages for the kernel you want to remove, including image, headers, etc.  But as mentioned it is a good idea to leave at least one of the previous kernels in case you later run into some issue with the one just installed.

I have noticed that sometimes the same kernel version updates multiple times, but not sure if changes were different compile options or additional modules or something else.  So having an additional kernel version helps if one of those updates of the same version breaks something for you.

---

