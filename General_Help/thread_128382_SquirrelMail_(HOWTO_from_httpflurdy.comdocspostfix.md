---
title: "SquirrelMail (HOWTO from: http://flurdy.com/docs/postfix/)"
date: 2006-02-11
forum: General Help
---

### Post by rensu on 2006-02-11
Im trying to configure squirrelmail:
/var/www/squirrelmail/config/conf.pl
and came to this command:
mysql://username:password@127.0.0.1/database
Question is this:
Does it create automatecally the datebase? Or i have to create it myself. If I do have to create myself it then how i can do it. Can someone help me please?:confused:

---

### Post by SWAT on 2006-02-11
Try using [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) first! [https://wiki.ubuntu.com/Squirrelmail?highlight=%28squirrel%29](https://wiki.ubuntu.com/Squirrelmail?highlight=%28squirrel%29)
Then you can also try reading the Squirrelmail documentation (just give it a try)

---

### Post by uopjohnson on 2006-02-11
I don't believe that squirrelmail requires a database at all... but if you want to create one then you will proably be best off installing phpMyAdmin which is a web based mysql administration utility. 
or if you want to you can log into mysql with 
```

mysql -u *user* -p

```
and create a database with
```

create database *dbname*;

```

---

