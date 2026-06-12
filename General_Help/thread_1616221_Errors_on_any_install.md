---
title: "Errors on any install"
date: 2010-11-07
forum: General Help
---

### Post by th1bill on 2010-11-07
Errors were encountered while processing:
I recently rebuilt my system and did a fresh install of Ubuntu 10.04. Now, everything I try to install returns the following errors. I have tried installing the troubled packages but I get the same errors. Any thoughts?
> th1bill@home:~$: command not found
th1bill@home:~$ sudo apt-get samba
E: Invalid operation samba
th1bill@home:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
subprocess installed post-installation script returned error exit status 10
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.2) ...
dpkg: error processing samba-common (--configure):
subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
samba depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.2); however:
Package samba-common is not configured yet.
samba depends on samba-common-bin; however:
Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.2); however:
Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
winbind depends on samba-commoNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
n (= 2:3.4.7~dfsg-1ubuntu3.2); however:
Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
grub-pc
samba-common
samba-common-bin
samba
smbclient
winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
th1bill@home:~$
__________________

---

### Post by P4man on 2010-11-08
Can you run and report the output of

```
sudo apt-get update
```

---

