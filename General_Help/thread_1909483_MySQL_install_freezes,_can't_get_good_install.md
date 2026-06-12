---
title: "MySQL install freezes, can't get good install"
date: 2012-01-15
forum: General Help
---

### Post by BobDull on 2012-01-15
Hello everyone,

I am on Ubuntu 11.10. I had been successfully running a LAMP server for personal development for 4 months, when I came across a bug that wouldn't allow PHP to load certain things. After much troubleshooting, I decided to uninstall my lamp server and re-install it, because I remember how quick it was last time.

Well, initially the re-install went fine. Then, when I was trying to access my MySQL database, I got the error:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysql/mysql.sock' (2)

So, I tried to fix that, but ended up trying to re-install MySQL. Upon trying to re-install MySQL via apt-get, everything goes smoothly until it gets to this line:

Setting up mysql-server-5.1 (5.1.58-1ubuntu1) ...

And it will just sit there forever. I let it sit for an hour and no progress. So, I force closed, then had to kill the /var/dpkg/lock problem that started because I force closed the packaging tool in the middle of the problem.

SO ---> then I purge and remove everything I can related to apache, mysql, php, and try and re-install. 

Same thing happens, hanging on mysql-server-5.1.

I have been googling and was up all night last night :-/ Please help. Thanks.

---

### Post by thale on 2012-02-26
I'm having the exact same issue.

---

