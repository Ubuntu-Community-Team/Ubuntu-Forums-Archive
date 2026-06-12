---
title: "Restore Applications and Folders to Unity Panel"
date: 2011-09-01
forum: General Help
---

### Post by Orcris on 2011-09-01
I was playing around with ccsm, and while I was changing settings, the applications and files options disappeared from the Unity launcher. How do I return them to the launcher?

---

### Post by Bobhuber on 2011-09-01
> **Orcris said:**
> I was playing around with ccsm, and while I was changing settings, the applications and files options disappeared from the Unity launcher. How do I return them to the launcher?
Use the preferences option in ccsm and reset unity to defaults then delete the following (hidden) files in your home directory.
.gnome .gnome2 .gconf .gconfd

Reboot

This will reset ALL UNITY DEFAULTS and you will have to reconfigure any changes you have made in CCSM.

---

