---
title: "need fake raid 5 help"
date: 2010-03-14
forum: General Help
---

### Post by 440corbon on 2010-03-14
I am trying to get raid 5 set up as storage. I have karmic with myth set up on primary drive and wish to just use raid 5 for storage with jfs filesystem.
 TIA

---

### Post by 440corbon on 2010-03-14
I set my drives for raid use. (Fd) but I think I'm having trouble getting mdadm```
desktop:~$ sudo apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-reportlab python-renderpm python-qt4-dbus python-reportlab-accel
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  mdadm postfix
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
  
```

---

### Post by 440corbon on 2010-03-14
I grabbed mdadm off my mythbuntu disk and am running the raid setup now. If anyone has questions or needs help I can document my install stp by step.

---

