---
title: "Compiled kernel missing /lib/modules/.../source dir"
date: 2009-07-16
forum: General Help
---

### Post by SteelWo1f on 2009-07-16
I have compiled the kernel using command:

fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 

When I install the resulting debs, there is no /lib/modules/linux-2.6.28.9-custom/source directory.

How do I get the source directory to appear there? I've looked at all the other kernels I've build and its normally there. So it must be some flag or make target that I just don't know about.

Thanks

---

