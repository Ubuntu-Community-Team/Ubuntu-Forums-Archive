---
title: "Kernel Panic - can't find sdb1? booting over USB..."
date: 2009-12-16
forum: General Help
---

### Post by jorx on 2009-12-16
Hi everybody,

Just randomly my linux mint box quit booting.   I've got it installed on an external USB hard-drive, and it's always worked fine, with the boot flag set to boot from sdb1.
Normally an internal harddrive will be "sda", and as a second hard drive, my external will be "sdb". 

But it just started giving me this error;
"Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown - block (0, 0)"

Upon trying recovery mode, it does give me a wee bit more information beforehand.
"cannot open sdb1..." And it mentions available drives; sda, sda1 - 3, and sr0.  

Where did my external sdb go? It still loads GRUB fine...

Help would be appreciated. Cheers,

Jorx

---

