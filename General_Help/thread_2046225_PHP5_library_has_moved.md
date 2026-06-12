---
title: "PHP5 library has moved"
date: 2012-08-22
forum: General Help
---

### Post by Silvernail on 2012-08-22
Oneiric
Gnome3

I have an emailer that runs from a 'cron' entry. Since it is usually in the back ground, I don't see the results much. To day I occation to run it from a command line. The message was sent but I  got this NEW error for each address.

> 
Message has been sent to: 
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/sqlite.so' - /usr/lib/php5/20090626+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0

Checking to see if the file existed, I find it has a different name.
> 
dave@Dafydd:~/tffrobot$ locate sqlite.so
/usr/lib/php5/20090626+lfs/pdo_sqlite.so
/usr/lib/seed-gtk3/libseed_sqlite.so
dave@Dafydd:~/tffrobot$ 


Is this known? Is the kosher? Should I worry?

---

