---
title: "fglrx and updating kernel"
date: 2011-09-30
forum: General Help
---

### Post by ligiopro on 2011-09-30
I'm currently using the fglrx driver from the x-swat ppa on lucid with kernel 2.6.32-33. If I am to update the kernel to 2.6.32-34 (or maybe something in the 2.6.35 branch), I understand that I have to remove the fglrx driver and reinstall it on the new kernel. However, I am wondering what would happen if I try to boot back into my old kernel with fglrx drivers compiled for the new kernel. Would I need to reinstall the fglrx driver each time I intend to use a different kernel version?

As well, would the ppa purge of the x-swat ppa perform the same function as removing fglrx in synaptic?

---

### Post by sumski on 2011-10-01
If you install newer kernel version, the older will still remain installed (as will fglrx kernel module for that kernel). Fglrx should get automatically recompiled for every kernel update (and this wont affect older modules).

---

