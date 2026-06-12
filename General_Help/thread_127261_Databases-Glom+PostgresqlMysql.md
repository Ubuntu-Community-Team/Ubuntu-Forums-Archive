---
title: "Databases-Glom+Postgresql/Mysql"
date: 2006-02-08
forum: General Help
---

### Post by xerman on 2006-02-08
hello there,

I'm trying to install a database server on my iBuntu (iMac G3 DV/SE, G3@400MHz) running Ubuntu Breezy PPC. I tried with MySQL+MySQL Administrator with no success, as the "mysql_install_db" always comes to an error.

So I checked GLOM+PostgreSQL as GLOM interface seemed sleek and easy to handle and Need Productivity ASAP. I installed the PostgreSQL 8.1 stuff through Synaptic, so did with GLOM. I tuned config files as stated in
 
[http://www.glom.org/wiki/index.php?t..._Configuration](http://www.glom.org/wiki/index.php?t..._Configuration)

and by doing this I could get farther on GLOM. But at the moment the App needs to create a database, as there is no database yet (fresh install) I always come out with the same error message:

"The database 'template1" could not be created. You might not have enough privileges to do that"

I wonder why is this, as I have assigned a passwd to user 'postgres' through "System-Administration-Users and Groups", then I su'ed 'postgres' and then created a user to handle databases with permissions to create new databases and create new users.

I'm pretty stuck now, as I checked Glom doc available at [www.glom.org](www.glom.org) (which is not much) and doc available at "www.postgresql.org".

I tried also to link OO.org Base to mysql or postgresql with no succes either so I'll keep on trying with all the stuff until I get something arranged.

By the way, I'm a newbie to Ubuntu, and so to Databases. But at least all that copy-paste stuff stated in those places "postgresql.org" and "glom.org" was done as said.

Thanks for any suggestion on getting Glom+postgresql  or mysql to work.

---

