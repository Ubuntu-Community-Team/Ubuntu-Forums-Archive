---
title: "Why Kernel Version is 2.6.32 After Upgraded to 12.04 LTS?"
date: 2012-09-11
forum: General Help
---

### Post by AlphaZeta on 2012-09-11
I just did two in-place upgrade (one 32 bit, one 64 bit) from 10.04 to 12.04. But for some reason, the kernel version is 2.6.32 (uname -a returns Linux dimensionx 2.6.32-38-generic-pae #83-Ubuntu SMP)? 

But a clean install of 12.04 shows that the kernel version is 3.2.0-30. Any ideas why the kernel is not updated when doing the in-place upgrade?

---

### Post by lukeiamyourfather on 2012-09-11
You can install whatever kernel you want from the repositories, but it probably leaves the kernel alone because changing it can break drivers and kernel modules that existed before the upgrade.

---

### Post by AlphaZeta on 2012-09-12
Ok... thanks. So it sounds like this is by design....

---

### Post by Bucky Ball on 2012-09-12
Are you saying it has remained at the 10.04 kernel on *both* machines? When you look in Software Sources, do you see the new 12.04 repositories there along with (possibly disabled) older 10.04 repos?

It shouldn't leave the kernel untouched. All drivers, apps, kernel modules etc should be upgraded to the current 12.04 LTS defaults and current kernel (-30) as part of the process.

---

