---
title: "GParted NTFS Resize"
date: 2011-06-17
forum: General Help
---

### Post by Marionumber1 on 2011-06-17
I want to resize my Windows 7 partition (yes more partition work) in the version of GParted I got from Ubuntu Software Center on 9.10. But there is a warning sign next to the device name, and a resize operation fails. It says there are bad sectors, but I've ran chkdsk /r /f and it still says that. Any ideas?

---

### Post by mikewhatever on 2011-06-17
It's advisable to resize W7 partitions from the Disk Manager in W7, as other non-native programs are known to cause problems. Have you tried the W7 disk manager?
A bad sector usually means that the sector is damaged, and a file system check simply marks it as such, but does not, and can not fix it.

---

