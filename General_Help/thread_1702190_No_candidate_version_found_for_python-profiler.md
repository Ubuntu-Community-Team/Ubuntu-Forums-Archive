---
title: "No candidate version found for python-profiler"
date: 2011-03-07
forum: General Help
---

### Post by yang on 2011-03-07
Help, I'm trying to install the Python pstats module but I get the following:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid

$ uname -a 
Linux dev 2.6.32-305-ec2 #9-Ubuntu SMP Thu Apr 15 08:05:38 UTC 2010 x86_64 GNU/Linux

$ sudo aptitude install python-profiler
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No candidate version found for python-profiler
No candidate version found for python-profiler
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

$ sudo aptitude install python2.6-profiler
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No candidate version found for python2.6-profiler
No candidate version found for python2.6-profiler
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

$ aptitude show python2.6-profiler 
No current or candidate version found for python2.6-profiler
Package: python2.6-profiler
State: not a real package

```

From another 10.04 machine (where I've successfully installed python-profiler in the past):

```

$ dpkg -L python-profiler
/.
/usr
/usr/lib
/usr/lib/python2.5
/usr/lib/python2.5/profile.py
/usr/lib/python2.5/pstats.py
/usr/lib/python2.6
/usr/lib/python2.6/profile.py
/usr/lib/python2.6/pstats.py
/usr/share
/usr/share/doc
/usr/share/doc/python-profiler
/usr/share/doc/python-profiler/README.Debian
/usr/share/doc/python-profiler/copyright
/usr/share/doc/python-profiler/changelog.Debian.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/python-profiler
/usr/share/pyshared-data
/usr/share/pyshared-data/python-profiler

```

Thanks in advance for any hints.

---

### Post by yang on 2011-06-15
Solution: had to add multiverse to /etc/apt/sources.list

Via: [https://bugs.launchpad.net/ubuntu/+source/python-profiler/+bug/537634](https://bugs.launchpad.net/ubuntu/+source/python-profiler/+bug/537634)

---

