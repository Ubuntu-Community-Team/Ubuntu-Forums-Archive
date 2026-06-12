---
title: "Do Not show Mounted Drive on Desktop"
date: 2009-09-25
forum: General Help
---

### Post by CrusaderAD on 2009-09-25
Is there anyway to not show the mounted drives on the desktop? I have the drives mounted through fstab. The desktop just gets cluttered.

---

### Post by alphaniner on 2009-09-25
If you mount them anywhere than /media, they will not show up on the desktop.  I use /mnt.

---

### Post by CrusaderAD on 2009-09-25
They're not mounted in media. I have them mounted in a directory I made in my home folder.

---

### Post by scouser73 on 2009-09-25
To Hide the mounted drive icons on your desktop please follow these instructions.

**1** - Press **Alt & F2** and enter this command: **gconf-editor**

**2** - Now browse down to the following key: **apps \ nautilus \ desktop**

**3** - You should see a key in the right-hand pane called **volumes_visible**. Remove the checkbox from it, and the icons will instantly disappear from the desktop. Remember that you can always access the drives from the &#8220;Computer&#8221; icon, or easily in the file browser.

---

### Post by keplerspeed on 2009-09-25
You sure can! Just open a terminal and enter:
```

gconf-editor

```
Then go to apps>nautilus>desktop and untick volumes_visible

EDIT beat me to it scouser!

---

### Post by CrusaderAD on 2009-09-25
Thanks! Worked perfect!

---

### Post by alphaniner on 2009-09-25
Doesn't that also make auto mounted usb drives and cd-roms not show up though?

---

### Post by CrusaderAD on 2009-09-25
It doesn't list them on the desktop if this is disabled. This doesn't bother me cause it fires it up in nautilus right away and lists it as well. Small price for a far less cluttered desktop.

---

