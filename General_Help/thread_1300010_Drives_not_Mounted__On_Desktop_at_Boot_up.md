---
title: "Drives not Mounted / On Desktop at Boot up"
date: 2009-10-24
forum: General Help
---

### Post by daldude on 2009-10-24
My drives are not automatically mounted or they are not on the desktop at boot up even if they were when I shut down after I first clicked on each of them to open them and mount them and display them on the desktop.
If I try to drag a drive to the desktop I get this error

There was an error copying the file into /home/dal/Desktop.
Can't open mountable file


I'm using 9.04 64-bit. I did not have this problem with 8.04 32-bit.:mad:

---

### Post by mikewhatever on 2009-10-24
In order for a drive to get auto mounted at boot, it had to be selected during partitioning and assigned a mount point. Another way is to add a line to fstab. However, I don't believe dragging an icon to the desktop should mount a drive. You should be able to see all of the drives, both mounted and unmounted, in the left panel of the file browser. Just click on the drive, an voila, it's mounted.

---

