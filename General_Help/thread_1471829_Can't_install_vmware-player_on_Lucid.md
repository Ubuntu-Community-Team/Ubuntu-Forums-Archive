---
title: "Can't install vmware-player on Lucid"
date: 2010-05-03
forum: General Help
---

### Post by fwiffo on 2010-05-03
When I try to install vmware-player it complains that it can't find the kernel headers for my running kernel (2.6.31-20-generic) to compile its modules. I did have this working on 9.10. No amount of googling revealed the name of the package I need to get this working in Lucid. Little help?

---

### Post by WorMzy on 2010-05-03
I don't know if it'll make any difference, but try using the latest kernel, 2.6.32-21-generic. You might need to reconfigure grub to get the new kernel to appear as a boot option.

---

### Post by fwiffo on 2010-05-03
That's very weird. I have the latest kernel installed but it wasn't in grub's menu.lst. I fixed that and now everything is fine. Thanks.

---

