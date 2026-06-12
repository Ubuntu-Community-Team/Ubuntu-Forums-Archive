---
title: "Dpkg error, cant update anything."
date: 2011-09-07
forum: General Help
---

### Post by Sanguine Helios on 2011-09-07
This is the error i keep getting in the terminal, update manager, and synaptic package manager.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I cant find any solutions anywhere....I need help.

---

### Post by Rubi1200 on 2011-09-07
Hi ans welcome to the forums :)

Open a terminal with Ctrl+Alt+T and copy/paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second one refreshes them.

---

