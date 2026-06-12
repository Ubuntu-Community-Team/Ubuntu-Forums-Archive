---
title: "update manager error"
date: 2009-07-28
forum: General Help
---

### Post by HATRED on 2009-07-28
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/cy.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.


any idea how can i fix this? :confused:

---

### Post by Soul-Sing on 2009-07-28
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by HATRED on 2009-07-28
Thanks :)

---

