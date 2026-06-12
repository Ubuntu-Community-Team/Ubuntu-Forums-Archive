---
title: "Can't update Ubuntu 11.10"
date: 2011-12-19
forum: General Help
---

### Post by soltero5965 on 2011-12-19
Hello since last nght i have been trying to update my Ubuntu 11.10 but it always show this message:

E:Problem parsing dependency Replaces, E:Error occurred while processing industrialtango-theme (NewVersion2), E:Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.


what could be the problem?
Thanks..

---

### Post by CaptinGoogle on 2011-12-19
It seems this "industrialtango-theme" is causing you trouble. Perhaps you should remove it and then run:

```
sudo apt-get update
```

---

### Post by wildmanne39 on 2011-12-19
Hi, try this I think it will fix your problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thanks

---

