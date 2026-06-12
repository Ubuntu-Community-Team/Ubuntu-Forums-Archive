---
title: "Windows not working under Virtual Box"
date: 2009-08-09
forum: General Help
---

### Post by niceguy123 on 2009-08-09
```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

and 

It did work in the past. 

I recently ran update manager, don't know if this has anything to do with this new siduatition.

error message in VB

```
Failed to open a session for the virtual machine MS WINDOWS XP.
Virtual machine 'MS WINDOWS XP' has terminated unexpectedly during startup.

```

details:

```

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {540dcfda-3df2-49c6-88fa-033a28c2ff85}

```

Any help would be appreciated.

---

### Post by howefield on 2009-08-09
Probably updated the kernel with your last updates, the error is telling you what to do, run in terminal

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Barafu Albino Cheetah on 2009-08-09
You have updated the kernel, but virtualbox kernel module did not update. reinstall virtualbox. no config purge is needed.

---

### Post by niceguy123 on 2009-08-09
Thanks, I reinstalled VB and now it works. 

But...

I am trying in installed MS office from a CD, but in mycomputer in windows I don't see my CD drive?

What should I do?

---

### Post by benerivo on 2009-08-09
In the settings fot that virtual machine, have you gone to the CD/DVDROM section and ticked 'Mount Drive' and 'Enable Passthrough'.

---

