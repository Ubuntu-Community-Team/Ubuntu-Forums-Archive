---
title: "&quot;Kernel driver not installed&quot; error every time on Virtual box"
date: 2010-07-28
forum: General Help
---

### Post by Irishpolyglot on 2010-07-28
Hi everyone!
Each time I try to run my Windows virtual box, I got this error:
> **Kernel driver not installed (rc=-1908)**

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
Which is fine, so I run *sudo /etc/init.d/vboxdrv setup* as requested and then it works. But I have to do this EVERY TIME I use Virtual box. This step takes a minute or two to do its thing, so it's quite time consuming.

Any ideas to make it permanent?
And yes, the DKMS package IS installed.

---

### Post by P4man on 2010-07-28
Make sure you have virtualbox-ose-dkms installed (assuming you are using the OSE version). Also wont hurt to reinstall it.

---

### Post by timgood on 2010-07-28
I had the same problem. After much scratching of head I solved it thus:

```
gksu gedit /etc/modules
```

Add line ```
vboxdrv
```

to list of modules to be loaded at boot time.

Robert should be your father's brother.

---

### Post by Irishpolyglot on 2010-07-28
Thanks for those two replies! The problem always happens after a reboot, so I'll let you know (and close the issue) after next one if these suggestions work!
Thanks :)

---

