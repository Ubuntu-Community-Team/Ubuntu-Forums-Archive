---
title: "Dependency error for Disk Utility and mdadm"
date: 2011-10-20
forum: General Help
---

### Post by JasonFWard on 2011-10-20
I need to report a bug.

The "Disk Utility" as shipped on Desktop Ubuntu depends on mdadm in order to fulfil its RAID functionality.

However, although "Disk Utility" is installed by default, mdadm is not installed by default.

This at best leads to a bad user experience, and at worst causes compounded errors as "Disk Utility" does not fail gracefully and considers that mdadm has completed successfully even when it is not installed, leading to misleading information being displayed in "Disk Utility".

---

