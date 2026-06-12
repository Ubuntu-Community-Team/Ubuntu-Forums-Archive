---
title: "&quot;Failed to load package list&quot; Help"
date: 2011-07-17
forum: General Help
---

### Post by mbyrd11 on 2011-07-17
I am getting this message

"E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened."

It says that it is a major problem. If anyone could please direct me to a link or anything would be greatly appreciated.

screenshot attached

---

### Post by sirspazzolot on 2011-07-17
Sounds like a problem I had a little while ago. Mine was caused by Chrome translation things or something, though, while yours seems to be some Ubuntu issue I guess. I think I solved it by deleting the trouble-making list files and then upgrading everything or something. Maybe I uninstalled Chrome until after updating, I don't remember. Sorry!

---

### Post by Rubi1200 on 2011-07-17
Open a terminal with Ctrl+Alt+T and copy and paste the following commands (to avoid errors and typos):

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes any corrupted package lists, the second one refreshes/updates them.

---

### Post by philescandon on 2011-07-18
Thanks Rubi1200- your advice worked,

Cheers,
P

---

### Post by Rubi1200 on 2011-07-18
> **philescandon said:**
> Thanks Rubi1200- your advice worked,

Cheers,
P
Hi and welcome to the forums philescandon :)

Glad I could be of assistance and that this worked for you.

---

### Post by onefish on 2012-05-30
This simple solution worked for me! Thank you.

---

### Post by Doug Fisherman on 2013-01-12
> **Rubi1200 said:**
> Open a terminal with Ctrl+Alt+T and copy and paste the following commands (to avoid errors and typos):

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```The first command removes any corrupted package lists, the second one refreshes/updates them.


Works for me too Xubuntu 12.10 Quantal

---

### Post by oldos2er on 2013-01-12
Old thread closed.

---

