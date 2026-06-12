---
title: "Linux Kernel 2.6.31-15"
date: 2009-11-23
forum: General Help
---

### Post by pjalegria on 2009-11-23
Hi

Help, cant update linux kernel 2.6.31-15... anyone else???

Thanks

---

### Post by pjalegria on 2009-11-23
Bump...

---

### Post by bodhi.zazen on 2009-11-23
> **pjalegria said:**
> Bump...

Perhaps it may help if you were to take the time to describe how it is that you are trying to install your kernel. Please describe what problem you are having or what error message you are getting.

---

### Post by pjalegria on 2009-11-24
I have got this error message:

> E: linux-image-2.6.31-15-generic: subprocess installed the post-installation returned error exit status 127
E: linux-backports-modules-2.6.31-15-generic: dependency problems - leaving unconfigured

---

### Post by Darael on 2009-11-24
Hmm... Try doing "sudo dpkg --configure -a" in a terminal to reconfigure any packages that failed to configure.  That way, it can ask any questions needed, and if it still fails, post us the output so we can see what's going on.

---

### Post by meson2439 on 2009-11-28
I installed that image through synaptics. However I cannot boot from it. May be due to me changing grub into the maintainers version. In the end, I just got rid of it. Is it critical to update to that image. I'm thinking of waiting for the next iteration instead.

---

