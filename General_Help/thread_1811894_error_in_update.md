---
title: "error in update"
date: 2011-07-25
forum: General Help
---

### Post by deb_123 on 2011-07-25
Hi, 
  I have Ubuntu 11.0 installed.It is giving following error during update:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/mirror.csclub.uwaterloo.ca_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Please look at this matter.

deb_123

---

### Post by plucky on 2011-07-26
> **deb_123 said:**
> Hi, 
  I have Ubuntu 11.0 installed.It is giving following error during update:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/mirror.csclub.uwaterloo.ca_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Please look at this matter.

deb_123

Welcome to the forum

Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
``` and then run ```
sudo apt-get update
``` and see if you can now the update.

Good Luck

---

