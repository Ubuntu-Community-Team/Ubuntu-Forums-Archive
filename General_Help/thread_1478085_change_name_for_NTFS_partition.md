---
title: "change name for NTFS partition"
date: 2010-05-09
forum: General Help
---

### Post by ieee488 on 2010-05-09
Ubuntu is calling my Windows partition **20 GB Filesystem** on the icon that is placed on the desktop.

How can I change this to say WindowsXP or something like that ?

---

### Post by sisco311 on 2010-05-09
Change the partition's label: System -> Administration -> Disk Utility

---

### Post by Ginsu543 on 2010-05-09
Or you can use GParted. Your choice. :)

---

### Post by ieee488 on 2010-05-10
Using  System -> Administration -> Disk Utility , the option to make any changes to the Windows partition was greyed out.

I didn't try GParted.

I booted into Windows gave the partition a name. It was previously blank.

---

### Post by Ginsu543 on 2010-05-11
The Windows partition may have been greyed out because it was mounted when you looked at it using the Disk Utility. Before you can make any changes to a partition, it must be unmounted. If you go into GParted, if a partition is mounted, there will be a locked icon next to it. You can unmount it by right-clicking on the partition and choosing the "Unmount" option. Once it is unmounted, you can change its name (or format it or whatever you want to do to it).

---

