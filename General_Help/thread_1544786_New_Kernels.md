---
title: "New Kernels"
date: 2010-08-03
forum: General Help
---

### Post by cj.surrusco on 2010-08-03
The newest kernel in the repositories is currently 2.6.32-24, while on kernels.ubuntu.com, you can already download a .deb of the 2.6.35 kernel. Why does it take so long for new kernels to be added to the repositories?

---

### Post by dcstar on 2010-08-03
> **cj.surrusco said:**
> The newest kernel in the repositories is currently 2.6.32-24, while on kernels.ubuntu.com, you can already download a .deb of the 2.6.35 kernel. Why does it take so long for new kernels to be added to the repositories?

Because many other things have dependencies on the released kernel version and there is a lot of work involved to recompile and then test every single one of these packages.

Feel free to volunteer for the various development groups to expedite the process, I'm sure they can all use the extra help.

---

### Post by snowpine on 2010-08-03
2.6.32 is, and always will be, the only supported kernel for Ubuntu 10.04 Lucid Lynx.

Future releases (10.10 and beyond) will have newer kernels.

Advanced users can install different kernels from other sources. If you do so, it's at your own risk, and you are responsible for troubleshooting/updates/security since you are not using the supported Ubuntu kernel.

Hope that clears it up. Unless you have a pressing and specific need for an alternate kernel, I recommend you continue to use the tested, trusted, and stable Ubuntu 2.6.32 kernel. :)

---

### Post by cj.surrusco on 2010-08-03
Thanks a lot for the answers. I just figured that when it was released on ubuntu.com, that all the dependencies would already be sorted out. I didn't realize that there was an extra step.

---

