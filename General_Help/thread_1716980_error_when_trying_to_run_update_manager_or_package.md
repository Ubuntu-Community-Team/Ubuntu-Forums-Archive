---
title: "error when trying to run update manager or package manager"
date: 2011-03-29
forum: General Help
---

### Post by perlex on 2011-03-29
I get this upon loading both update manager and package manager, its errors this message then just closes out.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by plucky on 2011-03-29
> **perlex said:**
> I get this upon loading both update manager and package manager, its errors this message then just closes out.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

The package list is probably corrupt.

Remove the list with ```
sudo rm /var/lib/apt/list/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
``` and then run ```
sudo apt-get update
``` to download a new list.

If you still have a problem,I would recommend changing the "download server" using **Software Sources** gui and select another download server.

Good Luck

---

