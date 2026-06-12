---
title: "Reiser4 patch 10.04 lk-2.6.32.24"
date: 2010-08-08
forum: General Help
---

### Post by davidogg on 2010-08-08
Ubuntu 10.04 + latest kernel 2.6.32.24

I need to recompile my kernel for Reiser4 support. I ran through menuconfig and stripped out everything I don't need, and monolithitised everything I do need. Set CPU to Athlon64-sse3. Tested the kernel for a few days to make sure all is well, now ready to patch and recompile...

uname -r
2.6.32.15+drm33.5

I don't know what this drm33.5 is, is this a Ubuntu patch? Will this conflict with reiser4-for-2.6.32.patch.bz2 or should I be using a vanilla kernel for this? Is ~.15+drm33.5 binary compatible with 2.6.32.24 [edit: with respect to kernel modules]?

Thanks

---

### Post by davidogg on 2010-08-11
Reiser4 is a go! This Abstract Industries kernel for 10.04 is the stock Ubuntu kernel with the Reiser4 patch from Namesys, full preemptive, file systems pulled into the kernel, NTFS with write support, and compiled for AthlonXP-sse3 or above (AMD 64-bit only)

[http://dl.dropbox.com/u/8630257/linux-headers-2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt_2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt-10.00.Custom_amd64.deb]("http://dl.dropbox.com/u/8630257/linux-headers-2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt_2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt-10.00.Custom_amd64.deb")
[http://dl.dropbox.com/u/8630257/linux-image-2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt_2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/8630257/linux-image-2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt_2.6.32.15%2Bdrm33.5-ai2010-8-reiser4-preempt-10.00.Custom_amd64.deb)

To use with Reiser4 you'll need to install libaal-dev, libreiser4-dev and reiser4progs (apt-get, synaptic, whatever)

---

