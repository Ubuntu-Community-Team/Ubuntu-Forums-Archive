---
title: "Exposing Multiple Cores to VM"
date: 2012-02-14
forum: General Help
---

### Post by afz12 on 2012-02-14
On one Acer 5920 notebook, Virtualbox will only expose 1 of its 2 CPU cores to any Virtual Machine (VM) whereas on another HP dv6 notebook, all 4 of its CPU cores get exposed to the VM - faster than only 1! I have the same VB settings on both machines but is there some other "trick" that will coax this older Acer notebook to expose both barrels? 

Thanks for any suggestions :)

---

### Post by lechien73 on 2012-02-14
It's possible that your older CPU doesn't have Virtualisation Technology (VT) extensions.

To check this, open a terminal window and run:

```
 cat /proc/cpuinfo | grep "vmx\|svm"
```

If your system supports VT, then you'll see **vmx** (for Intel processors) or **svm** (for AMD processors) in the list of flags.

If this returns no output, then your processor doesn't support VT, and so will only expose 1 core to Virtualbox no matter what you do.

---

