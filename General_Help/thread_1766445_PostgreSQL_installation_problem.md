---
title: "PostgreSQL installation problem"
date: 2011-05-24
forum: General Help
---

### Post by sans_b on 2011-05-24
Getting an error when installing postgresql with ```
sudo apt-get install postgresql
``` on 11.04

error output:

Setting up postgresql-common (114) ...
* Starting PostgreSQL 8.4 database server
* The PostgreSQL server failed to start. Please check the log output:
2011-05-24 11:06:02 CDT FATAL:  could not access private key file "server.key": Permission denied           [fail]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-8.4:
 postgresql-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                      E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by searchfgold6789 on 2011-05-24
I would try ```
sudo su
sudo dpkg --configure -a
```
Or,
```
sudo su
sudo apt-get install postgresql

```

---

### Post by sans_b on 2011-05-24
That did not work. Same error as before.

I fixed this by installing PostgreSQL from source.

---

