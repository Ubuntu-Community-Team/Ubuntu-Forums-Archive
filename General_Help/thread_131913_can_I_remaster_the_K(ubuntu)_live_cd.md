---
title: "can I remaster the K(ubuntu) live cd?"
date: 2006-02-17
forum: General Help
---

### Post by derrick1985 on 2006-02-17
Hey Everyone,

I was wondering if it is possible to remaster the Ubuntu live CD? There are a few programs that I want to demonstrate on a PC without installing it to the HD, problem is that a lot of these programs have to be compiled by source. If I were to take a fresh ubuntu install, compile the programs that I wanted to and take a few away that I don't need, can I make it into a live cd, or is this a pipedream?

Thanks

---

### Post by houseofmore on 2006-02-17
check out bootcd in the repo.  haven't used it myself, but sounds up that way.

"bootcd - run your system from cd without need for disks
Build an image of your running Debian System with the command bootcdwrite.
You can also build a bootcd ISO image via NFS on a remote System.
When you run your system from CD you do not need any disks. All
changes will be done in ram. To reuse this changes at next boot time
you can save them on FLOPPY with the command bootcdflopcp. If booting
from your CD-drive is not supported, booting from FLOPPY is possible.
It is possible to install a new system from the running CD with the
command bootcd2disk. Bootcd2disk can also find a target disk, format
it and make it bootable automatically. Bootcd also supports lilo,
grub, initrd root fs, devfs, transparent-compression ISO 9660 fs and
syslinux/isolinux."

---

