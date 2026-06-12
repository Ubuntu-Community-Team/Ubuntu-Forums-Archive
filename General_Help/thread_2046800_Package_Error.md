---
title: "Package Error"
date: 2012-08-23
forum: General Help
---

### Post by franklin_m on 2012-08-23
Hello,

System has been working fine until my last auto update. Now I get:

-----------------------------------------------------------
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

---

### Post by wojox on 2012-08-23
Run these two commands and post back the results franklin_m:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by franklin_m on 2012-08-23
Actually,

Saw this first in another post. Ran it and the error is gone. Thanks for giving me that other method.

Frank

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

---

