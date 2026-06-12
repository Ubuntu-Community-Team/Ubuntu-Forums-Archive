---
title: "DPKG Error Code  (1)"
date: 2011-12-12
forum: General Help
---

### Post by ttshivers on 2011-12-12
This error has been bugging me for a while now. The error first appeared a couple months ago after I installed some updates. It has not gone away. The error shows up after I update my system.

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up dictionaries-common (1.11.5ubuntu1) ...
Template parse error near `', in stanza #9 of /var/lib/dpkg/info/dictionaries-common.templates
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of ienglish-common:
 ienglish-common depends on dictionaries-common (>= 1.10.6~); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing ienglish-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iamerican:
 iamerican depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.
 iamerican depends on ienglish-common (= 3.3.02-5); however:
  Package ienglish-common is not configured yet.
dpkg: error processing iamerican (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    Errors were encountered while processing:
 dictionaries-common
 ienglish-common
 iamerican
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am running Ubuntu 11.10 64 bit. If you need any other information, I will be happy to provide it.

---

### Post by shakabra on 2011-12-12
Try 'sudo apt-get install -f' and post back with the result.

---

### Post by ttshivers on 2011-12-14
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up dictionaries-common (1.11.5ubuntu1) ...
Template parse error near `', in stanza #9 of /var/lib/dpkg/info/dictionaries-common.templates
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of ienglish-common:
 ienglish-common depends on dictionaries-common (>= 1.10.6~); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing ienglish-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iamerican:No apport report written because the error message indicates its a followup error from a previous failure.

 iamerican depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.
 iamerican depends on ienglish-common (= 3.3.02-5); however:
  Package ienglish-common is not configured yet.
dpkg: error processing iamerican (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 dictionaries-common
 ienglish-common
 iamerican
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

