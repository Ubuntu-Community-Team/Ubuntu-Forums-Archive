---
title: "phpmysql change USER password / configuration"
date: 2011-12-10
forum: General Help
---

### Post by ELMIT on 2011-12-10
I did not need to use phpmysql for a while, ...

A. So the first I saw after logging in as root was:

1. The phpMyAdmin configuration storage is not completely configured, some extended features have been deactivated

2. Connection for controluser as defined in your configuration failed.

3. Server running with Suhosin. Please refer to documentation for possible issues.

What am I supposed to do?


B. Change user's password for user abc in phpmysql
1. select database mysql
2. select table user
3. select record for user abc
4. change password field to:   vId*-170T{;k   and save it
5. select record for user abc again
6. change the function dropdown menu of the password to 
6.a MD5   
the password will be changed to:  a4591405bb17dbd55a10eb27ae3b09c3
6.b or password
the password will be changed to: *49A0F528BAD53509E0131783DAB4BA41B9988A44

goto a command line and type in:
$ mysql -u abc -p mydatabase
Enter password: 
ERROR 1045 (28000): Access denied for user 'abc'@'localhost' (using password: YES)

Note: A website using the database was stored on a hard disk which I lost. I have now the database, and I could get the htmls back, but I do not remember the password I used in my previous installation.

How can I solve that?

---

