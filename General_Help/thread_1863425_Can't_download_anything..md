---
title: "Can't download anything."
date: 2011-10-17
forum: General Help
---

### Post by LuisAlejandro17 on 2011-10-17
I can't install anything using the terminal, Ubuntu Software Center doesn't stop loading, and the update manager also does not work.I get this error message when attempting to find updates.
______________________________________________________________

An unresolvable problem occurred while initialing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E; Encountered a section with no Package:header, E:Problem
with MergeList /var/lib/apt/lists/
us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-
i386_Packages, E:The package lists or status file could not be parsed or opened.'
_________________________________________________________________


I also recieve the identical message when attempting to download something via the terminal using sudo apt-get install xxxxxx.
I know I can fix this by reinstalling ubuntu, but I would rather fix the problem the hard way to avoid having to back up over 200Gb of data.
I really appreciate any help,

       Thanks,
                 Luis

---

### Post by Rubi1200 on 2011-10-18
Hi and welcome to the forums :-)

Open a terminal and copy/paste the following commands:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

Post back with errors (if any).

---

### Post by LuisAlejandro17 on 2011-10-18
Thank you so much!
Now I can upgrade to 11.10.

---

### Post by Rubi1200 on 2011-10-20
You're more than welcome :)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

