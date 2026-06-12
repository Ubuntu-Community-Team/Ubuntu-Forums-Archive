---
title: "where are mysql table stored? (how to get them from old HD)"
date: 2011-06-06
forum: General Help
---

### Post by rhythmiccycle on 2011-06-06
my mother board fried, and so I got a new pc, I have to old HD hooked up, and can access all the old files.

How do I get the mysql tables that were saved. I just installed LAMP, and left every thing as default on the old PC.

I have some important stuff saved, please help?!

---

### Post by Apollo87 on 2011-06-06
Hello,

By default, all MySQL data should be stored in /var/lib/mysql .  In that directory there will be a directory for each databse you have.  If you are just using myisam tables you should be able to just copy the database directory out.

Also, when you go to restore the table, make sure you change the owner ship of all the files back to the mysql user, otherwise you may have problems starting mysql.

---

