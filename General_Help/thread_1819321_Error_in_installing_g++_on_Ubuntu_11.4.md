---
title: "Error in installing g++ on Ubuntu 11.4"
date: 2011-08-05
forum: General Help
---

### Post by bubblesppf on 2011-08-05
Hi I have been trying to install g++ complier on Ubuntu 11.4 (64- bit) and I happen to get the following error. 
```


user@ubuntu:~$ sudo apt-get install g++
[sudo] password for user: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


```

Can anyone help with it.

---

### Post by Rubi1200 on 2011-08-07
Hi and welcome to the forums :-)

Open a terminal and copy/paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes any corrupted package lists, the second one updates them again.

---

### Post by bubblesppf on 2011-08-08
thank you :)

---

### Post by Rubi1200 on 2011-08-09
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

