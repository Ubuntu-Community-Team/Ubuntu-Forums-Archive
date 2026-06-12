---
title: "I have to keep running these commands every reboot"
date: 2010-03-05
forum: General Help
---

### Post by altjx on 2010-03-05
For some reason, everytime I reboot my PC, I can't access any printers, I have to manually run ```
/etc/init.d/cups start
```

And then it start working... Then when I try running VirtualBox, I keep getting this message
```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

I'm not asking specifically about VirtualBox, but I'm starting to think this is a general problem with that folder or something? Anyone know why I have to keep running that command to start the printing service. Even when starting VirtualBOx 3.1 I have to rebuild the stuff for it to work

---

### Post by altjx on 2010-03-05
Hmm :\, pretty sure there's a simple fix out there somewhere?

---

