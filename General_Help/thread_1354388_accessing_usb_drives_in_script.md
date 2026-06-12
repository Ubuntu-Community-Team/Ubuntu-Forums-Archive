---
title: "accessing usb drives in script"
date: 2009-12-13
forum: General Help
---

### Post by duiu on 2009-12-13
So I'm working on an rsync script. I need it to automatically select the first or biggest USB drive connected to my system. However depending n the brand they get mounted in different folders in the /media/ folder. How can I determine what is a USB drive in a bash script?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
You'll have to set specific mount points in fstab so they always mount to the same point then add the mount points to your script.

---

