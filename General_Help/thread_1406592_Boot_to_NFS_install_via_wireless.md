---
title: "Boot to NFS install via wireless"
date: 2010-02-14
forum: General Help
---

### Post by megahurts on 2010-02-14
I've succesfully followed the various guides to allow me to boot any PXE capable PC on my home network into Karmic via PXE and NFS, what I'd really like to do is be able to boot my laptop the same way via wireless, obviously the WLAN card in the laptop doesn't support PXE boots, so I'm guessing I need to do something like the following:

Recompile the kernel to include the wlan/wifi drivers in the kernel rather than as modules. Have the resulting vmlinuz and initrd available bootable from the laptop, or from a USB drive, appending the NFS root mount point.  

Does this sound like right, and if not what am I missing?  I'm happy to go googling, but I'm not entirely sure what I'm looking for. ;)

---

