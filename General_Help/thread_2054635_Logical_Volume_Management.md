---
title: "Logical Volume Management"
date: 2012-09-07
forum: General Help
---

### Post by Enforcer83 on 2012-09-07
I am going through a re-install of unbuntu but before I re-install, I was wondering if the data stored on an LVM will be moved around as physical volumes (PV) are removed?

For instance, say I have an Volume Group (VG) that is 3.7 TB big made up of drives with sizes of 1 TB, 2 TB, 500 GB and 200 GB.  I have somewhere around 900 GB of data residing on this VG which had been set as my /home folder.  If data is residing on the 200 GB and 500 GB drives and I remove them, will the data be redistributed elsewhere in the VG before these drives are removed from the VG?

---

### Post by jerome1232 on 2012-09-07
I think this has the info you are looking for.

[http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

---

### Post by Enforcer83 on 2012-09-08
Tried your suggestion.  However, I have no extra extents to allow the VG to move data too.

Is there a way to move data without having extra space the VG can use?

---

### Post by jerome1232 on 2012-09-08
Nope, perhaps you can try shrinking your logical volumes down to the smallest size they can be while holding their data, to free up extents.

You have backups right?

---

