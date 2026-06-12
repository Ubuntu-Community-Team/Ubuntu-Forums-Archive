---
title: "Duplicate LInux Images after Update/Reboot"
date: 2011-09-18
forum: General Help
---

### Post by deepaknet on 2011-09-18
I just completed the Update Manager process and after reboot the Grub Menu shows

.33 Image 
.33 Image (recovery mode)

This two lines repeats for another older version

Two memory test modules

Windows XP

I would like to know how to remove that 'another old version'?

---

### Post by TeoBigusGeekus on 2011-09-18
Better keep it. It's just the previous kernel image; if something goes wrong with the latest one, you can always switch to the older kernel.
If, however, you insist, open synaptic package manager and search for linux-image.
Locate the older version, right click it and choose completely remove.
After that, open a terminal and do a
```
sudo update-grub
```
to update your grub (duh!) and you're done.

---

### Post by drs305 on 2011-09-18
If you want to keep the older kernel but hide it in the menu, you can use Grub Customizer, a great GUI app. Then, if your current kernel fails, you can press 'e' at the Grub menu and change to the earlier kernel.

To learn more about installing/running Grub Customizer, click the "Customizer" link in my signature line.

---

