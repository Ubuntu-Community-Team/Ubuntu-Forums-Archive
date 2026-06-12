---
title: "Samba, Samba-common, samba conf problem!!!!"
date: 2009-10-02
forum: General Help
---

### Post by meluzi02 on 2009-10-02
I really don't what to do about this problem of mine...

when i tried to update these error occurs:


[B]marvz@MARVZ:~$ sudo aptitude upgrade
[sudo] password for marvz: 
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  samba samba-common system-config-samba 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up samba-common (2:3.3.2-1ubuntu3.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3.2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-samba:
 system-config-samba depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing system-config-samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 samba-common
 samba
 system-config-samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba-common (2:3.3.2-1ubuntu3.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3.2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-samba:
 system-config-samba depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing system-config-samba (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
[COLOR=RoyalBlue] samba-common
 samba
 system-config-samba[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done[/B]

please i really need your help...thanks a lot

---

### Post by beastrace91 on 2009-10-03
Have you tried upgrading your system via the update manager? (Administration->Update Manager) Or if you really want to do it from terminal ```
sudo apt-get update
sudo apt-get upgrade
```

Does this upgrade method yield the same error?

~Jeff

---

