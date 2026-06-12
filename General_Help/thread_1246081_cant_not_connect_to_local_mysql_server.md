---
title: "cant not connect to local mysql server"
date: 2009-08-21
forum: General Help
---

### Post by manfer on 2009-08-21
I'm using ubuntu karmic koala. The last partial distribution upgrade done today made mysql server fail.

I knew something was going to be wrong as in packages it was showing it was going to delete mysql-server-core-5.0, mysql-server-5.0, ..., and one more related to mysql, but it was only going to install the update mysql-server-core-5.1.  ?????? That just sounded to me something was going to be wrong with mysql.

Now if I try to connect to mysql it is not working at all.

> 
can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock

What would be the best solution? If it is to install packages, which ones should I install?

I expect the databases will be intact after solving this problem.

---

### Post by manfer on 2009-08-21
I suppose installing the metapackage mysql-server should solve the problem (it should install mysql-server-5.1) but I would like to know the opinion of someone knowing how it would affect my system.

Databases, database users, ..., would be all still there intact?

---

### Post by manfer on 2009-08-21
Looking on packages I can see mysql-client-5.0 is not upgraded. Maybe this must be solved too installing mysql-client metapackage which should install mysql-client-5.1

I would like someone else opinion about all these.

---

### Post by manfer on 2009-08-21
Well, as databases are in there place intact, I did a backup and I'm going to try those packages installation and look what happens.

---

### Post by manfer on 2009-08-21
Worked like a charm.

As expected selecting both mysql-server and mysql-client metapackages marked mysql-client-5.0 for deletion, mysql-server-5.1 for installation and mysql-client-5.1 for installation. After the install process finished mysql is working fine again. Databases haven't been affected at all.

All this problem came from an upgrade on ubuntu karmic, maybe someone find same problem and this can help.

---

