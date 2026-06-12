---
title: "ubuntu-bug question update-manager"
date: 2011-08-21
forum: General Help
---

### Post by dgoodma on 2011-08-21
I am having an issue with the update-manger, I get this error: E: Encountered a section with no Package header, E: Problem with MergeList /usr/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages,E:the package lists or status file could not be parsed or open.
It says to file a bug against update-manager, so I enter ubuntu-bug update-manager ---- then it says it cannot gather information, no program.... 

How do I fix the update-manager?

---

### Post by jfed on 2011-08-21
Might not do much, but alot of the times I have issues with the gui update manager, try running this code

```
sudo apt-get update && sudo apt-get upgrade
```

When prompted for your password, enter it, that should update your packages.

---

### Post by dgoodma on 2011-08-21
I get when I run that command:
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Frogs Hair on 2011-08-21
You can try running these commands _one at a time_ .```
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get update

```

---

### Post by dgoodma on 2011-08-21
daryl@daryl-Presario-F700-GR967UA-ABA:~$ sudo apt-get clean
daryl@daryl-Presario-F700-GR967UA-ABA:~$ sudo apt-get autoclean
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by oldos2er on 2011-08-21
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by jediknight64 on 2011-08-22
> **dgoodma said:**
> I am having an issue with the update-manger, I get this error: E: Encountered a section with no Package header, E: Problem with MergeList /usr/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages,E:the package lists or status file could not be parsed or open.
It says to file a bug against update-manager, so I enter ubuntu-bug update-manager ---- then it says it cannot gather information, no program.... 

How do I fix the update-manager?

How do I get an update manager to appear is a better question. I just installed ubuntu 10.10 on a friends old sony vaio and the UM worked in 10.04, but now it will not show itself. It must grant me its updates! For I am frustrated. But I will not give up!

---

