---
title: "Ubuntu Software Center, Synaptic Package Manager &amp; Update Manager Error"
date: 2011-07-06
forum: General Help
---

### Post by arafu on 2011-07-06
My Ubuntu Software center keeps showing me the loading icon if I want to browse any category or search an item & nothing else happen.

If I want to run Update Manager a window says :

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

If I want to run Synaptic Package Manager a window says :

```
An error occurred

The following details are provided:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

If I type sudo apt-get update in terminal, at the end it says :

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

I can not install any .deb package, Neither I can update my system.. any solution please ?

---

### Post by RedSingularity on 2011-07-06
Its a known bug that is being worked on.  In the meantime, run the following command and see if it resolves it:

```
 sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
```

---

### Post by RedSingularity on 2011-07-06
The bug report in question is [Bug 346386.]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386")

---

### Post by arafu on 2011-07-06
Ok..So I havetyped :
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages

& the Output is:

rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages': No such file or directory

---

### Post by arafu on 2011-07-06
> **RedSingularity said:**
> The bug report in question is [Bug 346386.]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386")
Ok I am trying the solutions described there.. I'll post an update

---

### Post by RedSingularity on 2011-07-06
You had a space in the word binary.

"rm: cannot remove  `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_[COLOR=Red]***bina ry***[/COLOR]-i386_Packages': No such file or directory"

---

