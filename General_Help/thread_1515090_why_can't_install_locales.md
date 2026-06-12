---
title: "why can't install locales ?"
date: 2010-06-21
forum: General Help
---

### Post by zcrself on 2010-06-21
sudo apt-get install  locales

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  locales
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3338kB of archives.
After this operation, 13.2MB of additional disk space will be used.
(Reading database ... 134402 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.18.36_all.deb) ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18.36_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18.36_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bachstelze on 2010-06-21
You are trying to install the Dapper locales package, but the tzdata package, which is causing the conflict, does not exist in Dapper.

Which version of Ubuntu are you using?

---

### Post by zcrself on 2010-12-31
> **Bachstelze said:**
> You are trying to install the Dapper locales package, but the tzdata package, which is causing the conflict, does not exist in Dapper.

Which version of Ubuntu are you using?
```

Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty


```

---

