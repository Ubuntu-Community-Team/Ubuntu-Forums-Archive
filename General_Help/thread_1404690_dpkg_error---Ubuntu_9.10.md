---
title: "dpkg error---Ubuntu 9.10"
date: 2010-02-11
forum: General Help
---

### Post by dee02 on 2010-02-11
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Yes I tried 'sudo dpkg --configure -a'

Should I do a reinstall....HELP HELP....

"Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.31-17-generic
dpkg: subprocess installed post-installation script returned error exit status 1"

---

### Post by sandyd on 2010-02-11
you ran out of space on the ubuntu partition.
are you using wubi or did you install a dual boot? (seperate partitions)

---

### Post by dee02 on 2010-02-14
> **carlee said:**
> you ran out of space on the ubuntu partition.
are you using wubi or did you install a dual boot? (seperate partitions)

I install dual boot!

---

### Post by r_s on 2010-02-14
what is the output of df- h.

---

