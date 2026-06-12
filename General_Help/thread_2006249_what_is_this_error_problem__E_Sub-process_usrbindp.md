---
title: "what is this error problem : E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-06-18
forum: General Help
---

### Post by maizuddin35 on 2012-06-18
Hi guys! 

I hope post this thread in the right section..

what is this problem here..?
```
utm@utm-hp:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up isc-dhcp-server (4.1.ESV-R4-0ubuntu5.1) ...
start: Job failed to start
invoke-rc.d: initscript isc-dhcp-server, action "start" failed.
dpkg: error processing isc-dhcp-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dhcp3-server:
 dhcp3-server depends on isc-dhcp-server; however:
  Package isc-dhcp-server is not configured yet.
dpkg: error processing dhcp3-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 isc-dhcp-server
 dhcp3-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and what should I do ?

thanks in advanced.

---

