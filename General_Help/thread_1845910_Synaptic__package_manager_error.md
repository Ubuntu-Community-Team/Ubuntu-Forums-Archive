---
title: "Synaptic  package manager error"
date: 2011-09-18
forum: General Help
---

### Post by ashwin_nat on 2011-09-18
When i try to open synaptic package manager, it shows the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

What does this mean?? I tried sudo apt-get update. Even that failed. What do i do

---

### Post by garvinrick4 on 2011-09-18
Open a terminal and copy and paste these 3 commands one at a time.
```
sudo rm /var/lib/apt/lists/* -vf 
```
```
sudo apt-get clean all 
```
```
sudo apt-get update
```

---

