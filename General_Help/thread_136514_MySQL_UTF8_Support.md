---
title: "MySQL UTF8 Support"
date: 2006-02-26
forum: General Help
---

### Post by mrtnhndrkx on 2006-02-26
Hi, 

I need to import a database from another server. This database uses UTF8 and my default Ubuntu MySQL installation doesn't seem to have support for UTF8. 

Is there an (easy) way to change that so my MySQL - installation uses UTF8 as a default character set. 

Thanks, 
Maarten

---

### Post by adamvert on 2006-02-27
I'm pretty sure that MySQL 4.0 doesn't support character sets, so you need to update to 4.1:

sudo apt-get install mysql-server-4.1

should do the trick, and then you get character set and collation support.

Adam

---

