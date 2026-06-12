---
title: "problem with CP script"
date: 2010-07-28
forum: General Help
---

### Post by TomAbada on 2010-07-28
hi all
i need to make a script that will copy ANY flash drive i will plug in my computer to my Desktop
as SOURCE i wrote /dev/sdc   (like i see in GParted)
but that only copy a folder called "sdc" to my desktop

anyone know how i can make a general command that will copy any flash drive ill plugin without writing as SOURCE /dev/xxx ???


thanks in advance

---

### Post by prodigy_ on 2010-07-28
You're doing it wrong. /**dev/sdX** are block devices, not file systems, so you can't copy anything meaningful directly from them. You need to find the mount point of your flash drive first. Open terminal, run these commands: ```

sudo fdisk -l
mount
``` and post the output here.

---

Anyway, the command you're looking for should look like:```
cd /<path>/<your_USB_mount_point>; find . -depth -print0|cpio --null -pvd ~/Desktop/<new_directory_name>
```

---

