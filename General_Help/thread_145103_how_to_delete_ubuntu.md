---
title: "how to delete ubuntu?"
date: 2006-03-15
forum: General Help
---

### Post by marlis56 on 2006-03-15
I have Windows OS on drive C:\ and Ubuntu on drive D:\ and now would like to remove Ubuntu from drive D:\ including the GRUB boot so that Windows would automaticaly boot on startup. How can I remove Ubuntu from drive D:\ including the GRUB boot.

---

### Post by xiaoxin on 2006-03-15
imho big mistake deleting ubuntu hehehehe.

anyways 

Boot with the XP installation CD.

When prompted, press R to repair a Windows XP installation.

If repairing a host with multiple operating systems, select the appropriate one (XP) from the menu. If you have only one operating system, enter 1 to select it.

Enter the administrator password if prompted.

To fix the MBR, use the following command:

```
fixmbr
```

Type y and ENTER to fix the MBR.

Type exit to leave the recovery console and reboot.

After that you can just format drive D

---

