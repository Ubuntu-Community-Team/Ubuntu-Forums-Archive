---
title: "Error when running Update Manager"
date: 2009-08-07
forum: General Help
---

### Post by hbe14 on 2009-08-07
I'm getting the following error when running the update manager:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:problem with MergeList /var/lib/apt/lists/dm.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Anyone know how to fix this? I can't update if I don't. Thanks in advance.

---

### Post by Soul-Sing on 2009-08-07
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

