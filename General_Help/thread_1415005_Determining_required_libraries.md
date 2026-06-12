---
title: "Determining required libraries"
date: 2010-02-24
forum: General Help
---

### Post by Barticus on 2010-02-24
Is there a way to determine which libraries a package needs before installing the package itself?

---

### Post by patchwork on 2010-02-24
If it's in the repos you can check the dependencies from [http://packages.ubuntu.com](http://packages.ubuntu.com)

for example, to check the dependencies of the package adtool in the karmic repos:
[http://packages.ubuntu.com/karmic/admin/adtool](http://packages.ubuntu.com/karmic/admin/adtool)

shows the dependencies of:


[LIST]
[*][libc6]("http://packages.ubuntu.com/karmic/libc6")      (>= 2.4)         GNU C Library: Shared libraries      
also a virtual package provided by                 [libc6-udeb]("http://packages.ubuntu.com/karmic/libc6-udeb")
[*]            dep:     [libldap-2.4-2]("http://packages.ubuntu.com/karmic/libldap-2.4-2")      (>= 2.4.7)         OpenLDAP libraries
[/LIST]



EDIT:  Ah....mcduck's idea is much more elegant...

---

### Post by mcduck on 2010-02-24
Sure, run this in a terminal to check all dependencies of a package:

apt-cache show *packagename* | grep Depends

edit: or right-click the package in Synaptic, select Properties, and take a look at the Dependencies-tab. ;)

---

