---
title: "Error starting Update Manager"
date: 2012-05-18
forum: General Help
---

### Post by Bupkus on 2012-05-18
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Is there a fix?
Thanks.

Using:
Dell inspiron 1525 laptop
Ubuntu 12.04 upgraded from previous Ubuntu

---

### Post by drs305 on 2012-05-18
Remove that list and reload the repository list. You can do it by unchecking the problem repository in Ubuntu Software Center (Edit > Software Sources), Update Manager (Settings lower left) or Synaptic (Settings, Repositories).

Or open a file browser as root and remove the file:
```
gksu nautilus /var/lib/apt/lists
```
and delete "extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages"

---

### Post by Bupkus on 2012-05-18
Delete
"extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages.IndexDiff"
as well?

---

### Post by Bupkus on 2012-05-18
Deleted just that one file and all seems fixed.

Thanks.

---

