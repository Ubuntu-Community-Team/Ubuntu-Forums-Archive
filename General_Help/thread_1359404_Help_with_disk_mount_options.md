---
title: "Help with disk mount options"
date: 2009-12-19
forum: General Help
---

### Post by jimcott on 2009-12-19
I am running Jaunty with all the updates on my laptop. I had an additional disk plugged in to the CDROM port and its two partitions came up automatically in the "places" menu of Gnome. Since I wanted these partitions to open read-only. I tried to modify the mount options in the graphical menu by altering the mount options. Unfortunately, I did not do this correctly. Now, although the partitions atill appear on the "places" menu, anytime I try to click on the listed "IBM Laptop" partitions, I get an error "Cannot Mount Volume Invalid mount option when attempting to mount the volume 'IBM Laptop'.

I cannot locate where Gnome is getting the initialization, or figure out how to back out of my error. I would appreiciate any suggestions and/or help. THANK YOU IN ADVANCE.
Jim

---

### Post by spiderbatdad on 2009-12-19
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by dcstar on 2009-12-19
> **jimcott said:**
> I am running Jaunty with all the updates on my laptop. I had an additional disk plugged in to the CDROM port and its two partitions came up automatically in the "places" menu of Gnome. Since I wanted these partitions to open read-only. I tried to modify the mount options in the graphical menu by altering the mount options. Unfortunately, I did not do this correctly. Now, although the partitions atill appear on the "places" menu, anytime I try to click on the listed "IBM Laptop" partitions, I get an error "Cannot Mount Volume Invalid mount option when attempting to mount the volume 'IBM Laptop'.

**[B]I cannot locate where Gnome is getting the initialization**[/B], or figure out how to back out of my error. I would appreiciate any suggestions and/or help. THANK YOU IN ADVANCE.
Jim

Application-System Tools-Configuration Editor (gconf-editor)

Unset the keys under /system/storage/volumes/ that relate to the device.

---

### Post by jimcott on 2009-12-21
Thank you both for your suggestions, which were very helpful and informative.
Jim

---

