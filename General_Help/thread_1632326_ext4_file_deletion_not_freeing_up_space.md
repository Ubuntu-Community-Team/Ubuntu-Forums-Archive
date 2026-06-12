---
title: "ext4: file deletion not freeing up space"
date: 2010-11-27
forum: General Help
---

### Post by GuiGuy on 2010-11-27
I have an esata drive that is mounted in an esata connected docking station. The HDD is formatted as ext4. 

Deleting files from the HDD (using SHIFT + DELETE) is not freeing up space, despite gparted reporting there is free space. 

There are no permission issues preventing R/W access to the drive.

Any attempt to write even the smallest file to the HDD results in "disk full" errors. 

I have connected the drive directly to the motherboard's internal sata connectors and get the same error. 

HDD diagnostics report the drive as "healthy". 

Any ideas what else to try, short of backing up and reformatting the drive?

---

### Post by iNsOmNiOuS on 2010-11-27
Hey GuiGuy

In the / folder of that drive Press CTRL+H (shows hidden folders) and delete the folder called .trash-1000 or anything similar.

---

### Post by GuiGuy on 2010-11-27
> **iNsOmNiOuS said:**
> Hey GuiGuy

In the / folder of that drive Press CTRL+H (shows hidden folders) and delete the folder called .trash-1000 or anything similar.

Thanks, but I was already aware of that. It didn't apply in this instance; there are no hidden directories or files on the HDD AFAICS

Cheers.

---

