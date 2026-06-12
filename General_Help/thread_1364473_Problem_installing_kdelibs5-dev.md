---
title: "Problem installing kdelibs5-dev"
date: 2009-12-25
forum: General Help
---

### Post by jake55 on 2009-12-25
While trying to install kdelibs5-dev, I run into this:

```
jake@RENO:~$ sudo apt-get install kdelibs5-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs5-dev: Depends: libcups2-dev but it is not going to be installed
E: Broken packages
```An umet dependency on libcups2-dev. So I tried figuring out what the deal was with libcups2-dev:

```
jake@RENO:~$ sudo apt-get install libcups2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcups2-dev: Depends: libcups2 (= 1.3.9-17ubuntu1) but 1.3.9-17ubuntu3.1 is to be installed
E: Broken packages
```Which says I have version 1.3.9-17ubuntu1 but i need 1.3.9-17ubuntu3.1.  So I try to update my libcups2 and get:

```
jake@RENO:~$ sudo apt-get install libcups2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcups2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libkcddb4 libqt3-compat-headers libavfilter0 libqt3-headers libavdevice52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```What could I do? Is it possible to get kdelibs5-dev to install?

---

### Post by dcstar on 2009-12-27
> **jake55 said:**
> 
..........
What could I do? Is it possible to get kdelibs5-dev to install?

Do you have non-standard repositories?

---

### Post by mc4man on 2009-12-27
> Which says I have version 1.3.9-17ubuntu1 but i need 1.3.9-17ubuntu3.1. So I try to update my libcups2

Actually it means just the opposite, you have libcups2 (1.3.9-17ubuntu3.1) installed but the only -dev package available from your enabled sources is libcups2-dev (1.3.9-17ubuntu1)

devs and libs must usually be the same version # (=)

Check your sources and make sure under the update tab the first 2 are enabled (security and updates
System -> Admin. -> Software Sources -> Updates

(you're pretty far out of date anyway...
[http://changelogs.ubuntu.com/changelogs/pool/main/c/cups/cups_1.3.9-17ubuntu3.4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/cups/cups_1.3.9-17ubuntu3.4/changelog)

---

