---
title: "problem in update-manager"
date: 2011-10-20
forum: General Help
---

### Post by puneetsays123 on 2011-10-20
whenever i open my update manager it shows the following and closes thereafter. I have recently upgraded from 11.04 to 11.10.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by plucky on 2011-10-20
> **puneetsays123 said:**
> whenever i open my update manager it shows the following and closes thereafter. I have recently upgraded from 11.04 to 11.10.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Welcome to the forum

Open a terminal and run these commands ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command will delete the files in /var/lib/apt/lists/ and the second command will reload them from the repositories.

Good Luck

---

