---
title: "Location of MYSQL Databases - How to Find"
date: 2012-05-27
forum: General Help
---

### Post by Steve R. on 2012-05-27
I am looking into how to backup my compter including my database. According to a variety of posts and the file -> my.cnf, the database should be located in /var/lib/mysql. This directory has nothing in it, plus it has a little "x" in it. I suspect that the database has been migrated to another location. A search of the file system did not locate it.

I have PHDamin installed as well as Apache, I don't know if that has any effect on the location of the database. In fact, I was hoping that one of the PHP setting tabs would show the actual location of the database, but alas, NO.

I am using Ubuntu 12.02.

I am aware of "*mysqldump*", but that does not resolve the concern of knowing where the databases are actually located so that I can incorporate them into the backup program.

If MYSQL my database cannot be defined by a discrete location, is there a "*data*" directory that can be used by the backup program to capture asll MYSQL database?

---

### Post by Dave_L on 2012-05-27
You probably need to be root to access /var/lib/mysql:

```
sudo ls -l /var/lib/mysql
```

or

```
gksudo nautilus /var/lib/mysql
```

In my opinion, mysqldump is still the preferred way to backup the databases. You could have a script run it periodically to dump the databases to files, and then backup those files.

---

### Post by Habitual on 2012-05-27
> **Steve R. said:**
> ...the concern of knowing where the databases are actually located so that I can incorporate them into the backup program....

mysqldump doesn't care where the physical files for the DBs are.
mysqldump can occur anywhere on the Filesystem.

What "concern"?

---

### Post by Steve R. on 2012-05-27
Thanks-very much for the advice. Using sudo worked. Also thanks for pointing out that mysqldump would create a file that could be incorporated into the back-up process. Still learning.

---

### Post by Steve R. on 2012-05-27
In using "*sudo ls -l /var/lib/mysql*"; I saw that the group was "*mysql*".  I added myself to the group and used CHMOD to change the group permissions, now I can see the files.

Thanks again.

---

### Post by Dave_L on 2012-05-27
I would leave the mysql file permissions alone; changing them weakens security, and might also interfere with mysql's operation.

mysqldump can be run using the mysql root user if necessary, and the backup can be run as the Ubuntu root user.  That's the more conventional approach.

---

