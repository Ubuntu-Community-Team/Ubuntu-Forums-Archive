---
title: "All executables/scripts opening with Wine?"
date: 2009-11-22
forum: General Help
---

### Post by Mander on 2009-11-22
I don't really know what I have done, but it seems that now Ubuntu is trying to open *all* exectuable files or scripts with Wine.  For example, I downloaded [rockbox]("http://www.rockbox.org/wiki/RockboxUtility#Download") but when I unzip the installer and double click, it tries to open in Wine.  I tried ./, sh, and bash but I get various errors.

What have I done wrong?  Can I fix it?

TIA

---

### Post by SteveDee on 2009-11-23
> **Mander said:**
> I don't really know what I have done, but it seems that now Ubuntu is trying to open *all* exectuable files or scripts with Wine.  For example, I downloaded [rockbox]("http://www.rockbox.org/wiki/RockboxUtility#Download") but when I unzip the installer and double click, it tries to open in Wine.  I tried ./, sh, and bash but I get various errors.

What have I done wrong?  Can I fix it?

TIA

With Wine installed, "exe" files will be associated with Wine (i.e. if you right click on a .exe file in Nautilus, you will see that the default action will be "Open with Wine windows program loader"). You can change this by right click > Properties > Open With.

---

### Post by Mander on 2009-11-23
Yes, I realize that .exe files will be.  But .sh files and other scripts with no file extension are also trying to open with Wine, and I don't know what to change it to in Nautilus.

---

### Post by Mander on 2009-11-23
A friend helped me figure it out, finally.  The file was physically located on a shared NTFS partition, and it was messing with the executable permissions.  I moved it back to an ext3 partition and now it's fine.

---

