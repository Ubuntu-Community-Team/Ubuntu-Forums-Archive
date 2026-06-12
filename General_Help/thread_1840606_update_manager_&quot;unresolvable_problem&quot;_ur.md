---
title: "update manager &quot;unresolvable problem&quot; urgent help pls!!"
date: 2011-09-07
forum: General Help
---

### Post by imarubixcube on 2011-09-07
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

what should i do? i have to fix before the morning.

---

### Post by raja.genupula on 2011-09-07
i know one solution for this may its gonna help you 

```
sudo rm -rf /var/lib/apt/lists/*
```

then do

```
sudo apt-get update
```

---

