---
title: "startup manager error......."
date: 2009-07-27
forum: General Help
---

### Post by abhilashm86 on 2009-07-27
when i try syaptic or in terminal try to upgrade or update, this error is returned, why is startup manager failing to start?? so due to this, my update manager shows no updates, how to correct this?

```

abhilash@abhilash:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  k3b
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up startupmanager (1.9.11-1~hardy1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing startupmanager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 startupmanager
E: Sub-process /usr/bin/dpkg returned an error code (1)
abhilash@abhilash:~$ 


```

---

