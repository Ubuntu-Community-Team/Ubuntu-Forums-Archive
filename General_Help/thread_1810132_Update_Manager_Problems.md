---
title: "Update Manager Problems"
date: 2011-07-22
forum: General Help
---

### Post by fidelandche on 2011-07-22
I appear to be having a few problems with this release of Ubuntu (11.04) I was going to update the system and got the update manager to check for updates, it found 192 in total (11mb of updates) then my broadband kept dropping so I could not update. Now the broadband is sort of working for a short while, I have tried again to get the update manager to work but all I get is the following message; 

[I]Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/I] So what do I do?

---

### Post by Gremlinzzz on 2011-07-22
try terminal update
sudo apt-get update
sudo apt-get upgrade

---

### Post by fidelandche on 2011-07-22
I followed the advice in this post [http://ubuntuforums.org/showthread.php?t=1810124]("http://ubuntuforums.org/showthread.php?t=1810124") and all works.

---

### Post by wojox on 2011-07-22
Remove the corrupted files first:

```
sudo rm /var/lib/apt/lists/* -vf
```

> **Gremlinzzz said:**
> try terminal update
sudo apt-get update
sudo apt-get upgrade

---

