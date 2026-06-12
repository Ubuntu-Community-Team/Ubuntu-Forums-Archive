---
title: "Why do do you still have to unmount removable media?"
date: 2009-11-27
forum: General Help
---

### Post by daldude on 2009-11-27
Why does Linux still require one to un mount volumes even if they are not Linux  File Systems and are removable Flash FAT 16 or Fat 32 file systems?
Windows XP did away with having to use the Safely Remove Device on Jump Drives and compact flash cards and SD card and other Flash Media as well as USB Hard Drives by adding the option to sacrifice performance of the removable media in order to not have to worry about useing the safely remove option. It is very easy to forget to Unmount a removable Flash Device like a Jump Drive or Flash Media before pulling it out of the computer and if you do forget to unmount you will loose data or at least the last file you changed.

---

### Post by Aearenda on 2009-11-27
It's just a trade-off - speed of change while still plugged in, against the convenience of not having to tell it you've finished. Linux keeps the changes in memory, allowing fast manipulation of slow devices, until you tell it you're done, and then it flushes the buffers. Windows sends the changes out as soon as it can, which slows you the user down if you are making a lot of changes, and it also can result in unnecessary writes to a flash device that has a limit on how many changes it can do in its life.

---

