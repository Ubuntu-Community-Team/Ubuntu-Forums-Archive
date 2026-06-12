---
title: "synaptic package manager not opening"
date: 2011-08-26
forum: General Help
---

### Post by cbalasubramanian on 2011-08-26
Friends,
I installed ubuntu 11.04 successfully.  When i try to open synaptic pakage manager, it throws the following error. Someone please help to resolve the error.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Thanks,
Bala

---

### Post by cbalasubramanian on 2011-08-26
I have solved the issue. Sorry for posting without searching already posted questions.
The solution was the following


sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

This worked fine. Thanks to all those who share valuable informations.

---

### Post by Rubi1200 on 2011-08-29
Hi and welcome to the forums :-)

We're glad you found a solution.

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

