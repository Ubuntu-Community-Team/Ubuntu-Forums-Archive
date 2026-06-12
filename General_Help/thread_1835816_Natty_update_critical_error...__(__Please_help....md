---
title: "Natty update critical error... : (  Please help..."
date: 2011-08-30
forum: General Help
---

### Post by cadcam on 2011-08-30
I seem to be unable to use my update manager.....  this is the message i get when i open it.

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
"

Really?  This isn't very fun....  any help?

Thanks,

---

### Post by Rubi1200 on 2011-08-30
Hi,
open a terminal (Ctrl+Alt+T) and run the following commands (best to copy/paste to avoid errors):

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes any corrupted package lists, the second updates them.

---

### Post by DanneStrat on 2011-08-30
Deleted post.

---

