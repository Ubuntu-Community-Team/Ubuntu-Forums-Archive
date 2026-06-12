---
title: "serious error while opening the update manager"
date: 2011-05-29
forum: General Help
---

### Post by azhar ahmed on 2011-05-29
Hi,
this is azhar.
i encountered a serious error after installing ubuntu 11.04 while trying to open the update manager.
The error is:


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by TeoBigusGeekus on 2011-05-29
Rename the folder
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_faulty
```
and then
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```

---

