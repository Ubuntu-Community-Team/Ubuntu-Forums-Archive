---
title: "Issues with uncleared Windows Partitions?"
date: 2011-12-27
forum: General Help
---

### Post by cellorules on 2011-12-27
I accidentally moved all my Windows GRUB files onto an external drive and I didn't really want to go through the torture of figuring out how to fix it, so I just reformatted the drive and put on Ubuntu 11.04.

Recently a spoke to a man who had done something similar (clean-wipe and loaded Ubuntu 11), but he was having issues with Ubuntu because apparently there were still partitions of Windows that existed on the drive from the time of manufacture that cannot be removed with conventional software. Is this true? The man had his computer sent over to Washington somewhere where he had a relative of his wipe his drive with some intense software of some kind and reloaded Ubuntu 11.04 onto it and he said it has worked better than ever.

---

### Post by Bucky Ball on 2011-12-27
Boot from the install CD and 'Try Ubuntu'; 
Open Gparted (Partition Editor);
Right click and unmount any NTFS or FAT32 partitions left by the Windows install;
Mark them all for deletion;
Click 'Apply'.

You can delete all partitions this way, including Ubuntu ones (EXT*) so be careful. Don't delete any EXT* files unless you know for sure what's in them.

Not sure what you mean by 'Windows grub files'. Windows doesn't use grub so were you booting a Wubi install, not a hard drive/full install of Ubuntu?

---

