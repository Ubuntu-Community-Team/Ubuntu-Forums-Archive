---
title: "Can't configure mysql database"
date: 2009-07-10
forum: General Help
---

### Post by brewkakke on 2009-07-10
So, I've been trying to install some business software such as OpenERP or OBM (Open Business Management) and it's been impossible.  OpenERP had python-xml problems and when I got that fixed it couldn't connect to the localhost, so now I'm trying OBM and everything was going great during install, until it tried to configure it's mysql database.  

To break it down, a window pops up that says "Configure obm-storage" and there is a little checkbox that you check to "Configure database for obm-storage with dbconfig-common?".  After checking that and hitting "Next" it prompts you for your database admins password, which I had just set up earlier in the install process.  I enter it and it says that configuration failed.  Here's what it says in Synaptic:
```
Setting up obm-storage (2.1.10-0ubuntu2) ...
dbconfig-common: writing config to /etc/dbconfig-common/obm-storage.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using 
             old-style, non-debconf prompting. Ugh!

             Please inform the package maintainer about this problem.
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: Y
ES).
unable to connect to mysql server.
error encountered creating user:
ERROR 1045 (28000): Acesss denied for user 'root'@'localhost' (using password: Y
ES)
dbconfig-common: obm-storage configure: trying again.
```What is going on here?  It seems with all of the programs I've been dealing with I can't connect to the local host.  And maybe I'm a bit confused, but this is Ubuntu, there is no "root" user unless you grant them priviliges, which I'm the only user on this computer and I still use sudo.

---

### Post by nikgare on 2009-07-10
Are you sure you have installed the mysql server?

---

### Post by brewkakke on 2009-07-10
> **nikgare said:**
> Are you sure you have installed the mysql server?
Yes, it was a dependency for when I installed Open Business Management.  I just double checked Synaptic to make sure it was installed and sure enough it was.

---

### Post by brewkakke on 2009-07-10
Okay, problem is solved.  I had to completely remove OBM, mysql-server and it's dependencies.  I then installed mysql-server on it's own and set it up, then I installed OBM again.  So far, so good.

---

