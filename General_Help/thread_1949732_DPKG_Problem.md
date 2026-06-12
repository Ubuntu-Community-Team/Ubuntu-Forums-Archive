---
title: "DPKG Problem"
date: 2012-03-30
forum: General Help
---

### Post by anuragsachan07 on 2012-03-30
I am using Ubuntu 11.10. I got this problem since few days i searched over net but cant find any solution that worked for me.
-----------------------------------------------------------------
root@localhost:/home/anurag# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cvs (2:1.12.13+real-6ubuntu0.1) ...
Allowing use of questionable username.
Adding group `_cvsadmin' (GID 130) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 130 _cvsadmin' returned error code 10. Exiting.
dpkg: error processing cvs (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 cvs
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------------------------------------
Please help me..




Thanks & Regards
Anurag Sachan

---

### Post by Paddy Landau on 2012-03-31
Try these three commands:
```
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by raja.genupula on 2012-03-31
```
sudo rm /etc/group.lock
sudo rm /etc/gshadow.lock
```

then try again .

---

