---
title: "remove ubuntu"
date: 2011-03-02
forum: General Help
---

### Post by Mr.ALDO on 2011-03-02
I want to know how to remove ubuntu from my system it is on the same partition with windows XP and I want the XP alone 
I installed it using the ISO file burnt on a CD so I can't find the ubuntu removing option from add and remove inside windows control panel 
and also the windows installation CD is not available right now 

PLZ HELP

---

### Post by Captain Potter Fujichan on 2011-03-02
You can't have the two on the same partition, they're separate. Here is a site that explains how to remove it pretty well. Just follow it step-by-step. 
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by Mark Phelps on 2011-03-03
> **Mr.ALDO said:**
> I installed it using the ISO file burnt on a CD so I can't find the ubuntu removing option from add and remove inside windows control panel 
If you installed by booting from the CD, you most probably installed it to its own separate partition -- which is why you won't see it in Control Panel.
>  and also the windows installation CD is not available right now 
Well, that is a problem because you most probably overwrite the Windows MBR with GRUB. So, when you delete the Ubuntu partition, your PC won't boot anymore. Since you don't have the Windows CD, follow the link in the previous post to obtain the Hiren's Boot CD and use that.

---

