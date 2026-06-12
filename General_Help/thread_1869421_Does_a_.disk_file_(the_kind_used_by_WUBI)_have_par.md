---
title: "Does a .disk file (the kind used by WUBI) have partitions? If so, can I see them?"
date: 2011-10-25
forum: General Help
---

### Post by yanom on 2011-10-25
Wubi has root.disk and swap.disk files that it installs Ubuntu to. I wanted to see what their partition table is like, if they have one. I wanted to try to install other Linuxes to root.disk and use Wubi to boot them.

---

### Post by yanom on 2011-10-25
bump

---

### Post by oldfred on 2011-10-26
Short answer - No.

It is just a file inside the NTFS partition. Partitions are part of the drive not the file system in each partition.

You can only install one wubi per Windows. 

If you really want to multi-boot, create a 20 or 25GB logical partition for each system and a large NTFS partition for shared data with windows.

---

