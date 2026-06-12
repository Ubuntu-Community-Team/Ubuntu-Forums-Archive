---
title: "python2.6 minimal error after installing wine"
date: 2009-11-11
forum: General Help
---

### Post by deadred on 2009-11-11
Hi, been looking around for a solution to my problem and can't exactly find one.  For some reason, after installing wine, I can no longer update or install/remove any packages.

I believe the source of my problem is this (copied from terminal):

update-binfmts: /var/lib/binfmts/wine corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2

But i have no idea how to fix it, any help would be very much appreciated.

example of what i was trying to do:
```

hiram@Hiram-Linux:~$ sudo apt-get remove wine --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 wine-gecko ttf-tahoma-replacement ttf-symbol-replacement
  libmpg123-0 winbind
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 57 not upgraded.
3 not fully installed or removed.
After this operation, 55.7MB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up python2.6-minimal (2.6.4-0ubuntu2) ...
update-binfmts: /var/lib/binfmts/wine corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.6-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

solved:
just decided to do:
```

sudo rm /var/lib/binfmts/wine
sudo apt-get remove wine 
```
and that seems to have fix the issue.  can now update and install programs fine.

---

### Post by deadred on 2009-11-12
bump, could really use some help, would really like to avoid having to reinstall ubuntu.

---

