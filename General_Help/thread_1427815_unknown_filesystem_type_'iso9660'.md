---
title: "unknown filesystem type 'iso9660'"
date: 2010-03-12
forum: General Help
---

### Post by slk0 on 2010-03-12
I installed Ubuntu Server 9.10 in a virtual machine, and I'm trying to install the VMware Tools but I can't mount the installer CD:

$ sudo mount /dev/scd0 /media/cdrom
mount: unknown filesystem type 'iso9660'

Any help?  Thanks!

---

### Post by gmargo on 2010-03-12
Just install the **open-vm-tools** package instead. Maybe **open-vm-toolbox** for GUI tools too.

---

