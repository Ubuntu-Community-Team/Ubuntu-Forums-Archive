---
title: "error and cant update"
date: 2010-12-20
forum: General Help
---

### Post by cschamber on 2010-12-20
i am having an issue with updating, i try to update but get an error message as follows : 


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-proposed_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

what do i need to do to correct this issue ?

---

### Post by cschamber on 2010-12-28
is anyone able to help with this topic

---

### Post by Rubi1200 on 2010-12-28
Hi,
I apologize that you did not receive an answer to your post before now.

Anyway, from the terminal please run the following commands:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```If there are errors, copy/paste from the terminal and post them back here so we can try and narrow this down a bit.

Also, from the terminal:
```
 cat /etc/*release
```
Thanks.

---

