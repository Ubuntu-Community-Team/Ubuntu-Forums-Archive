---
title: "Getting VMWare Workstation 5.0 to run on breezy"
date: 2006-02-04
forum: General Help
---

### Post by rikard_grankvist on 2006-02-04
I'm having some problems with configuring the workstation on ubuntu. It complains about kernel issues and wants to build a custom module, but doesn't find the c header files etc. Does anyone have any experience with this? I've tried the vmware-any-any-update96, but it says there is no need to update.

---

### Post by homerhomer on 2006-02-04
hey use this?
[http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware)

enjoy,

once you get things going if you have an issue starting windows make sure that your network points to the complete address of your vmnet device, my was something like ethernet = vmnet1  and I changed it to ethernet = /dev/vmnet1 

good luck

---

### Post by rikard_grankvist on 2006-02-04
Thanks a lot! Extremely helpful. Didn't find that thread when searching for some reason.

---

