---
title: "Disk spindown with software raid"
date: 2009-11-21
forum: General Help
---

### Post by zuehls on 2009-11-21
When using software raid, is there an option to spindown the drives after a configurable period of inactivity?  I have this option on my Areca raid controller and am thinking of switching to software raid but want to know if I still have the ability to spindown the drives.

---

### Post by dcstar on 2009-11-23
> **zuehls said:**
> When using software raid, is there an option to spindown the drives after a configurable period of inactivity?  I have this option on my Areca raid controller and am thinking of switching to software raid but want to know if I still have the ability to spindown the drives.

Linux systems constantly write to various folders, so unless you are using your RAID array for storage totally outside of the system folders it is unlikely you will have an "inactive" time - ever.

---

