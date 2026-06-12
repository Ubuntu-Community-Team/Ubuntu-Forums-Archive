---
title: "Cant install anything..."
date: 2011-08-06
forum: General Help
---

### Post by dustcap on 2011-08-06
I always get these -


 Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


- when trying to install through Terminal.

And my Software Center doesnt work.

Help!!

---

### Post by Zill on 2011-08-06
> **dustcap said:**
> ... Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened...
dustcap:  Welcome to the forums.

Whenever you get an error like this it is always worth searching to see if someone else has resolved a similar problem.  For example, searching Google for "E: Encountered a section with no Package: header" returns about 73,700 results.  Looking at these results reveals that [Ubuntu FAQ #1591]("https://answers.launchpad.net/ubuntu/+faq/1591") may answer your question.  I would try running the three commands listed eg.
```
sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
```
followed, of course, by
```
sudo apt-get update
```

---

