---
title: "The server is not configured properly"
date: 2009-11-02
forum: General Help
---

### Post by Klazic on 2009-11-02
Hello all.

I have Ubuntu 9.10 for my VPS. I was having trouble installing MySQL -- I get an error: here is the full output.

```
root@sfwebhosting:/# sudo apt-get remove mysql-server
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mysql-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 98.3kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 109649 files and directories currently installed.)
Removing mysql-server ...
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
```I then ran the following command:
```
root@sfwebhosting:/# sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
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
```I got the same error from trying to remove MySQL server so I removed fuse-utils and gvfs-fuse using apt-get remove. But now when I try to login to my Ubuntu VPS I get: 'The server is not configured properly'. How do I fix this?

---

