---
title: "[update-manager] ubuntu 12.04 LTS"
date: 2012-08-20
forum: General Help
---

### Post by nphawat on 2012-08-20
While trying to run the update-manager, the following appeared:

*** Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/lb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'***

I am running ubuntu 12.04 LTS 64 bit.

Is this the correct place to report this problem ? what can i do to tackle it ?

---

### Post by oldos2er on 2012-08-20
Try ```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by nphawat on 2012-08-20
Thank you Ann. What you mentioned did solve the problem :)
If i am not mistaken, the first instruction mentioned did clean the source lists and the second initialized the manual update ?

---

