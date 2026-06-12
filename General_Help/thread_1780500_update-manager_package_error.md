---
title: "update-manager package error"
date: 2011-06-12
forum: General Help
---

### Post by Expatdiver1 on 2011-06-12
I am completely new at Ubuntu and would like to solve a problem I have when I try the update manager. I get this message:

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

I have also a problem with the Ubuntu Software Center & Computer Janitor: basically they will not load

Anyone can help with that?

---

### Post by Soul-Sing on 2011-06-12
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean all
sudo apt-get update

---

### Post by Matt__ on 2011-06-13
Open a terminal and type
```
sudo rm -rf /var/lib/apt/lists/*
 
```Enter your password. Then sudo apt-get update.

//pretty much should do the same as above, but not sure about the -vf parameter in the above post, but try it anyway :P

ps. if you get a /lists/partial is missing error
```
sudo mkdir /var/lib/apt/lists/partial
```

---

