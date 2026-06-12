---
title: "Please Help! Xorg using 540.6 mb of Ram"
date: 2009-07-09
forum: General Help
---

### Post by the2020 on 2009-07-09
Hi everyone, 
I recently upgraded my videocard to a ati raedon hd 3650. Anyways, Xorg is taking up way too much memory. Can you please also tell me what Xorg is for and is it necessary?

edit: Im using jaunty right now.

---

### Post by blazingbazoooka on 2009-07-09
> **the2020 said:**
> Hi everyone, 
I recently upgraded my videocard to a ati raedon hd 3650. Anyways, Xorg is taking up way too much memory. Can you please also tell me what Xorg is for and is it necessary?

edit: Im using jaunty right now.


Xorg is definitely necessary. Its basically the X window system, that allows a graphical environment (in Ubuntu its Gnome, Kubuntu KDE, etc) to run. Without it, its just CLI.  So yeah, you definitely need it. 


Can you post your specs and Xorg.conf?

---

### Post by pastalavista on 2009-07-09
You need to reconfigure Xorg for your new card. Boot in recovery mode and run the last option 'Repair X' and then reboot.

---

