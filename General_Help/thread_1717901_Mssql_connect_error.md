---
title: "Mssql_connect error"
date: 2011-03-30
forum: General Help
---

### Post by jetman5312 on 2011-03-30
I'm trying to read our companies mssql ordertracking db using php's mssql_connect. I was able to make this work when using WAMP, and I had done so by adding the same user on both machines and then applying that user name to the WAMP service. Because of viruses and poor performance... I moved the site over to ubuntu server... and I have to say i am very pleased, other than I cannot make a connection to mssql now. I installed sybase5 and can see mssql is available via phpinfo. It's using freetds. I know all my connection info is correct. I can ping the machine that has mssql from the new webserver. When i try to view a test php connection page it returns nothing but a null response, and my error log just says ERROR with no specific info. I did however find out that /tmp/freetds.log returns a bunch of jibberish. 

ubuntu forum isn't letting me submit the whole log, so i put it on sendspace here
[http://www.sendspace.com/file/a2dt3s]("http://www.sendspace.com/file/a2dt3s")

I did jack around with odbc_connect but still couldn't get it to work... I feel like I am close with mssql_connect but there is some user authentication problem. If anyone can offer up any helpful info on some trouble shooting or something to find out why it won't return any info from the mssql db i would appreciate it. Also I was wondering if something similar can be done with ubuntu where i applied a user to the WAMP service on my windows machine which then was able to connect to the mssql db. Anyways... I've been trying for a few days now, and really need some help. Thanks!

---

### Post by jetman5312 on 2011-04-01
K good news... for those of you who can't connect using mssql_connect.... i found another way that works perfectly for me on ubuntu 9.3 server with php 5.3.3-1 and apache2. 

Follow these two links and use something called PDO in place of mssql.

Link For Installation
[https://secure.kitserve.org.uk/content/](https://secure.kitserve.org.uk/content/) ... nd-freetds

Then use this link to try to figure out some of the programming to run queries and display data.
[http://net.tutsplus.com/tutorials/php/w](http://net.tutsplus.com/tutorials/php/w) ... se-access/

You can also refer to php documentation on it.
[http://www.php.net/manual/en/book.pdo.php](http://www.php.net/manual/en/book.pdo.php)

---

### Post by jetman5312 on 2011-04-01
realized links above dont work
reposting them

INSTALL LINK
[https://secure.kitserve.org.uk/content/accessing-microsoft-sql-server-php-ubuntu-using-pdo-odbc-and-freetds](https://secure.kitserve.org.uk/content/accessing-microsoft-sql-server-php-ubuntu-using-pdo-odbc-and-freetds)


Programming Reference link
[http://net.tutsplus.com/tutorials/php/why-you-should-be-using-phps-pdo-for-database-access/](http://net.tutsplus.com/tutorials/php/why-you-should-be-using-phps-pdo-for-database-access/)

---

