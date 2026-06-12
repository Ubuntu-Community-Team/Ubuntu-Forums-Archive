---
title: "SQL*Plus on Ubuntu 10.10"
date: 2011-10-15
forum: General Help
---

### Post by rotten69 on 2011-10-15
Hi everyone,

I've just installed SQL*Plus on my machine but I don't know how to log in..  I tried using my Oracle username and password but it was not working at all.  Where/How do I get a username and password?   Is it for free?   Can anyone please send me the link to registration page? 

cheers,

---

### Post by 2F4U on 2011-10-15
SQL*Plus is just a client to connect to your database. Where is your database located?

---

### Post by frozen.fire on 2011-10-15
You must have a database schema as suggested above. where is the database? is it on the same server?

---

### Post by rotten69 on 2011-10-15
Unfortunately, I do not have one. I'd like to create one though.  Can anyone point me to the right direction?


cheers,

---

### Post by rotten69 on 2011-10-16
Anyone please?

---

### Post by ratcheer on 2011-10-16
Please let us know what you're trying to do and we will be able to help you better.

Are you trying to get started learning about databases? Installing and running Oracle might be a big project. Why don't you try something like MySQL or PostgreSQL?

I'll help you if I can.

Tim

---

### Post by rotten69 on 2011-10-19
@ ratcheer,  I've installed SQLPlus on Linux. I want to get an account but I don't know how to do it and how much it'd cost me if it is not for free.

Cheers,

---

### Post by ratcheer on 2011-10-19
Uh, ok.

You see, SQLPlus is not something you use to access something out on the Internet. It is a tool for querying and manipulating Oracle databases. If you are in a home setting, most often you will have to be installing, configuring, and maintaining an Oracle database server. This is decidedly not a simple task.

If you are in a corporate environment, perhaps a DBA there would be willing to give you access to one of his databases. He might even create a special instance just for you.

Besides the SQLPlus client, you will also need some Oracle client network support software.

Your question has a much larger scope than you are thinking.

Tim

---

### Post by rotten69 on 2011-10-21
Yes, buddy. I am running my system in a home setting.  I want to install and configure oracle server. But, I have got no idea how to do it.   Any good tutorials about it that you may know of?

---

### Post by ratcheer on 2011-10-21
You could start here:

[http://www.oracle.com/technetwork/database/express-edition/downloads/index.html](http://www.oracle.com/technetwork/database/express-edition/downloads/index.html)

Good luck,
Tim

---

### Post by manojankk on 2011-12-03
I believe you do not have Oracle installed. In that case please refer
[http://sqlandplsql.blogspot.com/2011/12/installing-oracle-11g-on-ubuntu.html ]("Oracle installation on ubuntu")  

Or if you have Oracle installed and do not know how to connect sqlplus

1. Connect as oracle user
2. follow below steps
 
oracle@ubuntu$ sqlplus /nolog

It connect to SQL as idle instance. Execute below commands. Enter password created for sys at installation. Start database using startup command

SQL > 

SQL> connect sys as sysdba
Enter password: 
Connected.
SQL> startup
SQL> select count(*) from all_objects;

  COUNT(*)
   --------------
     70778

---

