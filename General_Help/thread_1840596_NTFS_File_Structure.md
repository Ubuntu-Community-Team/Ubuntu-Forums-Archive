---
title: "NTFS File Structure"
date: 2011-09-07
forum: General Help
---

### Post by trackmagic on 2011-09-07
I right-clicked properties on my new external HD to see if it is NTFS, but the menu does not say. Can somebody tell me how to tell what file structure is on it?

---

### Post by papibe on 2011-09-07
Using the GUI: Disk Utility.

On the terminal:
```
$ sudo mount -l
```
Hope it helps,
Regards.

---

### Post by JC Cheloven on 2011-09-07
Also ```
sudo fdisk -l
```

---

