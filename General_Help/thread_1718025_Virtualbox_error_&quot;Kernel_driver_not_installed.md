---
title: "Virtualbox error &quot;Kernel driver not installed (rc=-1908)&quot;"
date: 2011-03-30
forum: General Help
---

### Post by MollyWop on 2011-03-30
> Failed to open a session for the virtual machine Windows 7.
The virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1.

Kernel driver not installed (rc=-1908)
Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

I tried reinstalling everything in synoptics, restarting my computer, and even running modprobe vboxdrv in the terminal and nothing helps.

---

### Post by BigCityCat on 2011-03-30
Try installing dkms through synaptic.

---

### Post by BigCityCat on 2011-03-30
Also, you have to restart, go into set up (bios) and enable virtualization support.

---

