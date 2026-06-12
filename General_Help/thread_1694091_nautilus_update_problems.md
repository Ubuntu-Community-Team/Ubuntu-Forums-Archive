---
title: "nautilus update problems"
date: 2011-02-23
forum: General Help
---

### Post by COKEDUDE on 2011-02-23
I am having trouble updating nautilus. I think my problem lies in these 2 packages libappindicator1 and libdbusmenu-glib1. Can someone please tell me how I can fix this problem. I only have 2.30.1. When I downloaded the deb file it complained about libappindicator1. libappindicator1 complained about libdbusmenu-glib1. Apt-get thinks libdbusmenu-glib1 is already updated so I don't understand what the problem is. 

[http://packages.ubuntu.com/maverick/nautilus](http://packages.ubuntu.com/maverick/nautilus)

~ $ sudo apt-get install libappindicator1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libappindicator1

~ $ sudo apt-get install libdbusmenu-glib1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdbusmenu-glib1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

~ $ sudo apt-get upgrade nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic linux-headers-generic-pae
  linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

---

### Post by COKEDUDE on 2011-02-23
This might be useful. 

~ $ sudo dpkg -i "/libappindicator1_0.2.9-0ubuntu1_i386.deb"
Selecting previously deselected package libappindicator1.
(Reading database ... 203698 files and directories currently installed.)
Unpacking libappindicator1 (from .../libappindicator1_0.2.9-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libappindicator1:
 libappindicator1 depends on libdbusmenu-gtk1 (>= 0.3.12); however:
  Version of libdbusmenu-gtk1 on system is 0.2.9-0ubuntu3.1.
 libappindicator1 depends on libindicator1; however:
  Package libindicator1 is not installed.
dpkg: error processing libappindicator1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libappindicator1

---

