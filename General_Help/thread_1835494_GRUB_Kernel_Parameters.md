---
title: "GRUB Kernel Parameters"
date: 2011-08-29
forum: General Help
---

### Post by steevven1 on 2011-08-29
With Ubuntu 11.04 (I believe this means GRUB 1.99, but correct me if I'm wrong), when you want to specify TWO kernel parameters in /etc/default/grub, do you use a comma or what? Do you put a space after the comma? For example:

GRUB_CMDLINE_LINUX="i915.i915_enable_rc6=1, i915.i915_enable_fbc=1"

Thanks.

---

### Post by mcduck on 2011-08-29
Just separate the different parameters with a space (so no comma).

---

