---
title: "Could not initialize the package information."
date: 2011-05-02
forum: General Help
---

### Post by msmallard on 2011-05-02
I am currently running Ubuntu 11.04...When trying to update/install anything I get this message:

-----------------------------------------------------------------

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report..'
----------------------------------------------------------------------

Any help would be appreciated!

---

### Post by jzhang04 on 2011-05-02
I have the same problem. What should I do now?

---

### Post by Rinshan on 2011-05-03
I found a solution here: [http://www.linuxforums.org/forum/debian-linux/51937-aptitude-problem-problem-mergelist.html](http://www.linuxforums.org/forum/debian-linux/51937-aptitude-problem-problem-mergelist.html)

Run this:
```
sudo rm /var/lib/apt/lists/* -vf
```(backup before using!).

---

### Post by Bucic on 2011-05-09
A dozen topics on the same issue. I hope they will make the updater less susceptible to such corruption.

---

