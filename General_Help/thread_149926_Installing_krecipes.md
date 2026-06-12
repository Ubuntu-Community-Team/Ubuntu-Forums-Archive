---
title: "Installing krecipes"
date: 2006-03-24
forum: General Help
---

### Post by LotsOfPhil on 2006-03-24
Hi, I am trying to install krecipes. I type "sudo apt-get install krecipes" and get...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  kdelibs-bin kdelibs-data kdelibs4c2 krecipes-data libarts1c2 libavahi-qt3-0
Suggested packages:
  khelpcenter
Recommended packages:
  perl-suid akode
The following NEW packages will be installed:
  kdelibs-bin kdelibs-data kdelibs4c2 krecipes krecipes-data libarts1c2
  libavahi-qt3-0
0 upgraded, 7 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B/22.4MB of archives.
After unpacking 70.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 19392 package `libsndfile1':
 `Depends' field, syntax error after reference to package `libc6'
E: Sub-process /usr/bin/dpkg returned an error code (2)

Can anyone tell me how to get it to work?

---

### Post by claydoh on 2006-03-25
Try the following command:

> sudo dpkg --clear-avail 

It looks like a corruption or error in the file /var/lib/dpkg/available. This command clears that file, and when you update again it will repopulate the file.

---

