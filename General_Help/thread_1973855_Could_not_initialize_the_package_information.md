---
title: "Could not initialize the package information"
date: 2012-05-05
forum: General Help
---

### Post by Fayaz427 on 2012-05-05
hello everyone..
I have installed ubuntu 12.04 LTS yesterday....... and when I open update manager, it shows me error as
"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
please help me to fix this urgently.....

---

### Post by gnuisgreat on 2012-12-16
sudo rm /var/lib/apt/lists/* -vf 

sudo apt-get update

---

### Post by ibjsb4 on 2012-12-16
+1 on that gnuisgreat

---

