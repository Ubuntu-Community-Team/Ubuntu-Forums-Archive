---
title: "CPU Load Mirror Image"
date: 2010-02-04
forum: General Help
---

### Post by FraggedLocust on 2010-02-04
I was just wondering why my Dual-core Processor shows basically a mirror image where CPU core loads cross. On something like a file transfer, shouldn't they both be at the same level?

---

### Post by mk1w86 on 2010-02-04
CPU core loads vary all the time, as far as I know if one thread is higher priority more resources will be dedicated to the core the thread is running on and the other will loose those resources and cause the load to decrease.

When transferring a file only one core will be used because using two would be inefficient and probably slower because the thread has to keep switching cores.

---

