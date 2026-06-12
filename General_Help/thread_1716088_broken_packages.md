---
title: "broken packages"
date: 2011-03-27
forum: General Help
---

### Post by thisisonlyaname on 2011-03-27
I am using ubuntu 10.04 gnome

broken packages: 
kdelibs5
libplasma3

I get this error when i try to fix the packages:
E: /var/cache/apt/archives/kdelibs5-data_4%3a4.4.5-0ubuntu1_all.deb: unable to create `/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/column.gap.index.xml.dpkg-new' (while processing `./usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/column.gap.index.xml')

I use this to try to troubleshoot: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

At step 4, I get this error:

huuuh@ubuntu:~$ sudo fuser -vvv /var/lib/dpkg/lock
Cannot stat file /proc/2363/fd/29: Permission denied
Cannot stat file /proc/2363/fd/41: Permission denied

How can I fix the broken packages?

---

