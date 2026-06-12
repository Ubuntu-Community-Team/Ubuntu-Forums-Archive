---
title: "Pysdm mounts drives differently to normal?"
date: 2011-03-10
forum: General Help
---

### Post by ..sam.. on 2011-03-10
I have a partition with my firefox profile that when I mount with Pysdm it cannot access.
But when I mount normally by right clicking, unmount/mount. I can.
 
Any thoughts would be appreciated?

Thanks.

---

### Post by doas777 on 2011-03-10
well, the nautilus rightcick mount, is a userspace mount that uses the fstab. the pysdm seems to avoid using the fstab, but uses udev in a way that makes me believe it must be run as root. have you tried running it with gksu?

---

### Post by ..sam.. on 2011-03-10
I'm slightly new to all this.
How would I do that?

---

### Post by ..sam.. on 2011-03-10
I ran pysdm from the terminal using 'gksu psydm' if that is what you meant?

Unmounted and mounted with pysdm, made no difference.

---

### Post by doas777 on 2011-03-10
is this partition NTFS perhaps? if so, "permissions" are handled by options in fstab, so mounting it without fstab as pysdm does, it may not appropriately assign you the priv you need.

---

### Post by ..sam.. on 2011-03-11
its fat32.
I have removed pysdm and all its configurations. 
I am just going to edit the files myself as per: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

thanks for your help.

---

