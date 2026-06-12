---
title: "Difference between SUSE and Ubuntu"
date: 2010-10-01
forum: General Help
---

### Post by monokle on 2010-10-01
Hi All,

I am not sure where to categorize this question, but any help is very welcome. The situation is that we inherited a MySQL database and a PHP database application, both of which were developed on SUSE Linux. 

Not having a SUSE Linux machine ourselves (or able to afford the fees), I had wondered if it would be at all possible to host this thing on an Ubuntu machine. 

The specific build was:

[LIST]
[*]Apache 2.0.5.9 (Linux/SUSE)
[*]MySQL 4.1.13 with pdo_mysql 4.1.113
[*]PHP 5.2.2
[*]PEAR 1.7.2
[*]Pear DB_DataObject 1.8.7
[*]Zend Framework 1.0.2
[*]Smarty 2.6.14
[/LIST]
I believe that since Ubuntu can run all these components, that it is possible, but before I begin building this machine, I had wanted to check with you experts first. The only issue I can think of is a different file configuration of SUSE and Ubuntu (but I do not know enough about Linux to be certain).

Any help is very much appreciated.
Thanks!

---

### Post by gandaran on 2010-10-01
> Not having a SUSE Linux machine ourselves (or able to afford the fees), I had wondered if it would be at all possible to host this thing on an Ubuntu machine
what do you mean not able to afford the fees? suse linux is just as free as ubuntu is! (except the enterprise edition)
as to your problem I think there shouldn't be any, just export the database to the ubuntu server.

---

### Post by wojox on 2010-10-01
OpenSUSE is free. SUSE Linux isn't. 

As gandaran stated, make a copy of everything and port it over. There shouldn't be a problem.

---

### Post by monokle on 2010-10-05
Thank you both,

I'll post the results once we build the machine (on an old PPC box). But thanks for confirming the OS compatibility

---

### Post by AlexDudko on 2010-10-05
There is of course a compatibility between SuSe and Ubuntu, since they are both linux. But there could be some incompatibility between versions of your soft. For instance, MySQL 4.1.13 is a very old one, so there (not obviously) could be some issues. Everything can be solved by editing php scripts. Mind also the methods of backing up your MySQL data (depends upon the database engine) and restoring it on a new machine, and directory/file permissions.

---

