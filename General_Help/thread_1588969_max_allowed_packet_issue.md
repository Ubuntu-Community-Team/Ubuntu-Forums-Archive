---
title: "max_allowed_packet issue"
date: 2010-10-05
forum: General Help
---

### Post by zombiedvt on 2010-10-05
Hi I'm new to the Ubuntu and Linux community. I really love what you've guys, perhaps some girls as well, have done and accomplished. I'm very new to all this and I'm still learning.

This is my issue, I'm trying to import a sql file into my mysql database. The first thing I tried is to use phpmyadmin to import the sql file, but that returned:
```
'mysqldump: Error 2020: Got packet bigger than 'max_allowed_packet'
```So I changed the my.cnf file and set the value to 1G (which is the maximum if I'm correct). But still I get this error. So I tried directly importing the sql file through the shell with this commands:

```
mysql -u root -p db1 < olddb.sql
mysql --max_allowed_packet=1G -u root -p db1 < olddb.sql
```Both still return the same error and it seems like it doesn't have any effect when changing the values within the my.cnf file. I've also restarted the mysql process, hmm and I've tried lots of other things. So I'm not sure where the problem is exactly, I hope one of you more experienced unix guru's can help me out, or any other one who knows what the problem is :D!

Thanks

---

### Post by zombiedvt on 2010-10-06
Can anybody help me out please?

I've been trying for a few hours today and still no luck. Tried splitting the sql file, and then importing, but it was basically the same! Weird.

---

