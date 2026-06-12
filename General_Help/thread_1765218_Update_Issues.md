---
title: "Update Issues"
date: 2011-05-22
forum: General Help
---

### Post by brandonslayne on 2011-05-22
I keep getting this message, but i have no idea what to do to solve it. 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by amauk on 2011-05-22
```
sudo rm -f /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by brandonslayne on 2011-05-23
you are a life saver, thank you

---

