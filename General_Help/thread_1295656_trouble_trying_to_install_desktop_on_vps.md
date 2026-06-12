---
title: "trouble trying to install desktop on vps"
date: 2009-10-19
forum: General Help
---

### Post by monsterfish on 2009-10-19
i issued this command 
```
sudo apt-get install ubuntu-desktop
```
 and i got this error

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fuse-utils (2.7.4-1.1ubuntu4) ...
creating fuse group...
udev active, skipping device node creation.
 * Reloading kernel event manager...                                            No /sbin/udevd found running; none killed.
                                                                         [fail]
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on fuse-utils; however:
  Package fuse-utils is not configured yet.
dpkg: error processing gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 fuse-utils
 gvfs-fuse
E: Sub-process /usr/bin/dpkg returned an error code (1)
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fuse-utils (2.7.4-1.1ubuntu4) ...
creating fuse group...
udev active, skipping device node creation.
 * Reloading kernel event manager...                                            No /sbin/udevd found running; none killed.
                                                                         [fail]
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on fuse-utils; however:
  Package fuse-utils is not configured yet.
dpkg: error processing gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 fuse-utils
 gvfs-fuse
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


been googling and search this forum for hours but havent see any solution yet
any help would be appreciated.
P.S my experiment with Ubuntu has been 3 days -__-
thank you

---

### Post by abijma on 2010-01-22
i got the same problem. Did you already solved the problem? If so I like to hear from you how i can solve this problem. Thanks in advance!!

---

### Post by chad_v on 2010-03-03
This happens because udevd is not running and the 2 packages expect it to be running.  I got the same error when installing ubuntu-desktop on a VPS server.

After you get the error, just do as root (or with "sudo" in front of them):

```
/sbin/udevd &
```

That will start udevd running in the background.  Then just run:

```
dpkg --configure --pending
```

That worked for me.  I hope it helps you as well.

-Chad

---

