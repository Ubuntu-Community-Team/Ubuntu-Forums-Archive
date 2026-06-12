---
title: "MySQL error 2002 :  Mysql does not restart"
date: 2011-12-07
forum: General Help
---

### Post by spindler on 2011-12-07
I am getting an error with MySQL and it is down.   The error is:

[SIZE=3]*#2002  Cannot log in to the MySQL server.... Connection for controluser as defined in your    configuration failed.*[/SIZE]


I cannot log into the mysql system.   I tried to restart MySQL  using the following command.
[B]
[FONT=Courier New][SIZE=4]sudo service mysql restart[/SIZE][/FONT][/B]

It took a while but the command eventually finished... then I checked to see if it is running using the following command.

**[FONT=Courier New][SIZE=4]sudo netstat -tap | grep mysql[/SIZE][/FONT]**

Nothing happened..... I expected to see a table describing the mysql but it did not come up.  So I think it is not running. 

I attempted to reinstall Mysql but this did not fix the problem. 

Any idea what is going on?   What could have broken?  What do I do to fix this issue?

---

