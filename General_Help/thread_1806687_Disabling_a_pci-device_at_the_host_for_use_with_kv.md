---
title: "Disabling a pci-device at the host for use with kvm"
date: 2011-07-18
forum: General Help
---

### Post by Mesqualito on 2011-07-18
Hi,

I have a problem with disabling kernel modules via /etc/modprobe.d/blacklist.conf in Ubuntu.
I have tried it serveral times, by writing "blacklist MODULNAME", and by writing "install MODULNAME /bin/true" ( which should be another method ), into the configuration file. 
I've also done a update-initramfs -u, also no chance of disabling the modules.

I don't know if there exists another method to block modules in Ubuntu or if I forgot to block something else.
Hope you can help me with that!


P.S. As the title says, I need to stop the host system to load a pci-device ( avm fritz card) because it should be used by a virtual machine.

---

