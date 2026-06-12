---
title: "nfs-common configure/dependency problem"
date: 2011-02-08
forum: General Help
---

### Post by Memorice on 2011-02-08
Basically I have the same problem as described here: [http://ubuntuforums.org/showthread.php?t=708029]("http://ubuntuforums.org/showthread.php?t=708029"). Unfortunately none of the proposed solutions work. Below I list the output for each of them:

> user@machine:~$ sudo dpkg --configure -a
Setting up nfs-common (1:1.2.0-4ubuntu4.1) ...
start: Job failed to start
invoke-rc.d: initscript statd, action "restart" failed.
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nfs-common
 nfs-kernel-server

user@machine:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nfs-common (1:1.2.0-4ubuntu4.1) ...
start: Job failed to start
invoke-rc.d: initscript statd, action "restart" failed.
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nfs-common
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

user@machine:~$ sudo dpkg --configure -a
Setting up nfs-common (1:1.2.0-4ubuntu4.1) ...
start: Job failed to start
invoke-rc.d: initscript statd, action "restart" failed.
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nfs-common
 nfs-kernel-server

user@machine:~$ sudo dpkg -r nfs-common
(Reading database ... 245325 files and directories currently installed.)
Removing nfs-common ...
stop: Unknown instance: 
stop: Unknown instance: 
stop: Unknown instance: 
Processing triggers for man-db ...
Processing triggers for ureadahead ...

user@machine:~$ sudo dpkg --configure --force-configure-any -a
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not installed.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nfs-kernel-server


---

### Post by microtechno on 2011-02-28
I am having the same problem, if anyone knows a solution that would be great.

EDIT: I found a solution at [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2000136.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2000136.html)

```
sudo service idmapd stop
```

then ran
```
sudo apt-get install nfs-common
```

This caused my ssh terminal to hang as nfs restarted, so i restarted the computer and ran 

```
sudo dpkg --configure -a
```

and now everything works fine

---

