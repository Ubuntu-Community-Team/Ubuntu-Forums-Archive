---
title: "Transferring partitions to new computer"
date: 2011-11-26
forum: General Help
---

### Post by Xades on 2011-11-26
I have a new computer with Win7 but I need to transfer my Linux and WinVista partition to it. I have access to the Linux partition  but I can not boot to Windows because of bad sectors (I can still access the files through Linux). I just want to save as much data as I can migrate to the new system.

---

### Post by dino99 on 2011-11-26
[http://www.twm-kd.com/linux/cloning-ubuntu-linux-the-easy-way/](http://www.twm-kd.com/linux/cloning-ubuntu-linux-the-easy-way/)

---

### Post by dcstar on 2011-11-26
> **Xades said:**
> I have a new computer with Win7 but I need to transfer my Linux and WinVista partition to it. I have access to the Linux partition  but I can not boot to Windows because of bad sectors (I can still access the files through Linux). I just want to save as much data as I can migrate to the new system.

Plug the old disk into the new PC, use **gparted** to make space on the new disk for the old partitions and then use **gparted** or **ddrescue** to copy the old partitions to free space on the new disk.

---

### Post by Xades on 2011-11-26
How do I handle the WinVista partition? The new computer will have Win7 and I want to just take out the important files like my books and manga.

---

### Post by jerrrys on 2011-11-26
clonezilla may be what you want

[http://clonezilla.org/](http://clonezilla.org/)

---

