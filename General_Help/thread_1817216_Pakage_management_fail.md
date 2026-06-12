---
title: "Pakage management fail"
date: 2011-08-03
forum: General Help
---

### Post by hijiz on 2011-08-03
whenever i try to use any way to install a pakage it wont work and in terminal, upgrade manager, and synaptic the following message apears > Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/co.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Please help

---

### Post by plucky on 2011-08-03
> **hijiz said:**
> whenever i try to use any way to install a pakage it wont work and in terminal, upgrade manager, and synaptic the following message apears 
Please help

From a terminal ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```


The first command will delete all the list files including the one that is giving the problem, and the second command will download and restore a new set of list files.

Good Luck

---

### Post by hijiz on 2011-08-03
Thanks

---

