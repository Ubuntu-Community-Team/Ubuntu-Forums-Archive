---
title: "kernel nvidia updates fail"
date: 2006-06-24
forum: General Help
---

### Post by DoctorMO on 2006-06-24
I have this issue on my computer and 2 other machines I help support.

The computer says that there is an update, you try and install the updates and it fails.

when I do an apt-get upgrade  to find out whats wrong I get the following:

> 
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  nvidia-kernel-common
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
E: The package index files are corrupted. No Filename: field for package nvidia-kernel-common.


Has anyone else experienced this problem?

---

### Post by flyingbrass on 2006-06-24
I'd try:

sudo apt-get update
sudo apt-get dist-upgrade

My kernel and restricted modules were "kept back" too until I did a dist-upgrade.

---

