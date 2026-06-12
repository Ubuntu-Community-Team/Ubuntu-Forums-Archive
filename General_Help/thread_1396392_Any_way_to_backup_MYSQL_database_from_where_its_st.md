---
title: "Any way to backup MYSQL database from where its stored?"
date: 2010-02-02
forum: General Help
---

### Post by asusx on 2010-02-02
Hey guys,
I had a problem with my ubuntu installation, but I don't want to get into that... [-(   The OS wouldn't load...


Now, that I have a ubuntu partition mounted on a live cd, is there a way I can access or backup my database without booting the system?? I'm pretty sure the database is stored somewhere, but how can I find it and back it up?

---

### Post by Mip5 on 2010-02-02
> **asusx said:**
> Hey guys,
I had a problem with my ubuntu installation, but I don't want to get into that... [-(   The OS wouldn't load...


Now, that I have a ubuntu partition mounted on a live cd, is there a way I can access or backup my database without booting the system??
Yes - you can mount the hard drive, and you should be able to see your data. If you need to the MySQL data, it would probably be best to install MySQL in the live CD (maybe phpmyadmin too), and do a MySQLdump of your databases (rather than trying to copy a bunch of files from MySQL directories).

---

### Post by asusx on 2010-02-02
Well, the hard drive is mounted but I have no idea where the database is stored, I haven't backed it up at all.. How can I do mysqldump if I don't have the database?

---

### Post by Robster2 on 2010-02-02
The MySQL database is stored in in /var/lib/mysql/

---

### Post by cutout33 on 2011-03-07
Hello,

I have the same problem.

did you figure out how to backup the db?

Thanks in advance

---

### Post by leg on 2011-03-07
If you have phpmyadmin you can use it to me create a .sql file.

---

### Post by Habitual on 2011-03-07
Physically copying the intended db name (example: /var/lib/mysql/asusx_db) you can

```
cp -pr /var/lib/mysql/asusx_db /path/to/backup/directory
```

or use mysqldump to get an .sql file with

```
mysqldump -uroot -pmysqlpassword asusx_db
```

---

### Post by Habitual on 2011-03-07
> **asusx said:**
> Well, the hard drive is mounted but I have no idea where the database is stored, I haven't backed it up at all.. How can I do mysqldump if I don't have the database?

```
ls -hal /var/lib/mysql/*
```
will show you the databases as they are named.

---

### Post by Habitual on 2011-03-07
> **asusx said:**
> Well, the hard drive is mounted but I have no idea where the database is stored, I haven't backed it up at all.. How can I do mysqldump if I don't have the database?

```
ls -hal /var/lib/mysql/*
```
will show you the databases as they are named, and their sizes in [MG]

---

