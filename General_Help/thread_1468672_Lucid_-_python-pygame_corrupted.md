---
title: "Lucid - python-pygame corrupted"
date: 2010-05-01
forum: General Help
---

### Post by crossy on 2010-05-01
Using Lucid 32bit (full version, not beta or RC) on an Acer 5315 laptop which unfortunately powered-down during a software install. Even since then I've got problems installing or admin-ing software, for example:```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-pygame (1.9.1release-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-pygame (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-pygame
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried reinstall of python-pygame, purge, remove etc but nothing seems to work. Anyone got any magic incantation to fix this, otherwise I'm going to have to redo the OS install - which seems a little drastic to me.

Cheers, Bob.

---

