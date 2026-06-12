---
title: "Folders won't open"
date: 2009-09-04
forum: General Help
---

### Post by Awkward on 2009-09-04
I just did a fresh install of Ubuntu 9.04 on an empty harddrive, the install went fine, i can launch any program i want/perform updates.. butt none of the folders in my Places menu will open. I click on the icon for my Home Folder for example and the hourglass just spins but theres no effect, any ideas whats causing this? The install is pretty useless if i cant access the filesystem

---

### Post by oldos2er on 2009-09-04
If you open a terminal (Applications, Accessories, Terminal) and type in **nautilus**, does anything come up?

---

### Post by drs305 on 2009-09-04
Awkward,

Welcome to Ubuntu and the Ubuntu forums.

In nautilus, try right clicking on any folder, Open With, Other Application: File Browswer and see if that fixes it.

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Awkward on 2009-09-04
> **oldos2er said:**
> If you open a terminal (Applications, Accessories, Terminal) and type in **nautilus**, does anything come up?

It says "segmentation fault"

---

### Post by oldos2er on 2009-09-04
Do you have a blank CD or DVD in a removable media drive? If so, remove it, and try running Nautilus again.

---

### Post by Awkward on 2009-09-05
> **oldos2er said:**
> Do you have a blank CD or DVD in a removable media drive? If so, remove it, and try running Nautilus again.

The drives were empty

---

### Post by wojox on 2009-09-05
Here:

```
sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
```

---

### Post by Awkward on 2009-09-05
> **wojox said:**
> Here:

```
sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
```

That didnt do anything as far as I can tell, terminal asked my for password but no commands showed up in the window or anything, and the folders are still not functional.

Ps. I appreciate all the replies guys :)

---

