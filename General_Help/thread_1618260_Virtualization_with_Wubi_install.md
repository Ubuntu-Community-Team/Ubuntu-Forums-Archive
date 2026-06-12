---
title: "Virtualization with Wubi install"
date: 2010-11-10
forum: General Help
---

### Post by hamayoun on 2010-11-10
Hi

If I install Ubuntu via Wubi, can I then bring up the Windows partition through virtualization?  Or does virtualization only work for a dual boot system?  TIA.

---

### Post by bcbc on 2010-11-10
No. Wubi is not intended for this purpose. In most cases, wubi creates a virtual disk on the windows partition and so this partition is already mounted and in use.

---

### Post by Mark Phelps on 2010-11-10
> **hamayoun said:**
> Hi

If I install Ubuntu via Wubi, can I then bring up the Windows partition through virtualization?
No ... Wubi installs Ubuntu INSIDE the Windows partition -- so it would not make sense to then try to mount it inside of itself.

>   Or does virtualization only work for a dual boot system?  TIA.
IF you mean that you have Windows and Ubuntu installed in separate partitions, and you then want to run Virtualbox in the Ubuntu partition to mount the Windows OS -- I've read that CAN be done -- but it results in all kinds of corruption in the process.

---

