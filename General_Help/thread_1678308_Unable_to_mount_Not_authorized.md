---
title: "Unable to mount Not authorized"
date: 2011-01-30
forum: General Help
---

### Post by scrapper82 on 2011-01-30
After a sudo apt-get update/upgrade under Ubuntu Lucid Lynx i got the following errors:

Unable to mount "Device Name" not authorized.

So my user rights have suffered after the upgrade.

Other problems which appeared:
in Gnome Shut Down -> only performed a logout not a shut down.

On System -> Administration -> User and Groups after clicking Advanced Settings nothing happens.
No Password entry appears nothing...

Solution:
open a console/terminal. type

```

sudo users-admin

```now a programm starts with the proper rights. you can add your proper users rights.
such as: Mount user-space file system (FUSE) etc.

Now your system should work properly again.

i posted the solution on a german forum in german language as well: [http://forum.ubuntuusers.de/topic/unable-to-mount-not-authorized/](http://forum.ubuntuusers.de/topic/unable-to-mount-not-authorized/)

greetings
scrapper

---

### Post by scrapper82 on 2011-02-01
well unfortunately this is an ongoing bug. and with my method in the previous post it was just fixed for some reboots.
now it happens again. awkward. 

seems to be this bug: [https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139](https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139)

good luck
scrapper

---

