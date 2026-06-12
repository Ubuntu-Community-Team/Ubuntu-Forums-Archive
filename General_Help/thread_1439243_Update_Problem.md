---
title: "Update Problem"
date: 2010-03-25
forum: General Help
---

### Post by Niloc on 2010-03-25
When I do 'sudo apt-get update' I get
Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.cs.umn.edu_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

What is the solution?

---

### Post by Sin@Sin-Sacrifice on 2010-03-26
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade

---

### Post by slotto on 2010-05-02
Thanks!

---

