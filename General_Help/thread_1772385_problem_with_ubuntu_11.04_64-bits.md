---
title: "problem with ubuntu 11.04 64-bits"
date: 2011-05-31
forum: General Help
---

### Post by Davidlosung on 2011-05-31
I have a problem with my package managers  when ever I use a package manager, here is the message I get:

aptitude search aircrack-ng
[ ERR] Reading package lists
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
[ ERR] Reading package lists
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened

please help me I can't install anything anymore on my system

---

### Post by Rubi1200 on 2011-06-01
Hi and welcome to the forums :-)

Try this in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by Davidlosung on 2011-06-05
thanks it worked

---

### Post by Rubi1200 on 2011-06-05
> **Davidlosung said:**
> thanks it worked
Excellent! Glad you got it sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

