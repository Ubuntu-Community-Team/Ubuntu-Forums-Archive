---
title: "Apt-get can't remove some programs. Please help."
date: 2006-06-07
forum: General Help
---

### Post by acolic on 2006-06-07
Hi,

for some reasons apps that have been installed with apt-get can't be removed.

For example,  I've been trying to remove phpmyadmin from my system. I did a apt-get remove mysql and it correctly tried to remove phpmyadmin as well. But I got the following error when it tried to remove phpmyadmin:

/var/lib/dpkg/info/phpmyadmin.prerm : line 12 db_get: command not found
dpkg: error  processing phpmyadmin (--remove)
subprocess pre-removal script returned error exist status 127

When I try to remove gforge-db-postgresql I get:

head: cannot open '/var/lib/postgres/data/postmaster.pid' for reading: No such file or directory
kill: usage: kill [-s sigspec | -n signum | -sigspect] [pid | job]... or kill -1 [sigspec]
dpkg: error processing gforge-db-postgresql (--remove):
subprocess pre-removal script returned error exit status 1

I have tried to reinstall both apps and then remove them and I got the same errors.

Any ideas?

Thanks

Alex

---

### Post by thasheep on 2006-06-07
It's looking for a pid (process id of something running) file. Try starting phpmyadmin and then removing it. I'm guessing it can be started by doing something like 'sudo /etc/init.d/phpmyadmin/start'.

---

### Post by acolic on 2006-06-07
I'll try that when I get home tonight but phpMyAdmin is a php web application so I don't know why it would have a pid. It relies on Apache and MySql to run and both were removed fine.

Alex

---

### Post by acolic on 2006-06-08
Hi,

worked great. I had to fix some things in the pre-remove scripts but the software finally was removed.

Alex

---

