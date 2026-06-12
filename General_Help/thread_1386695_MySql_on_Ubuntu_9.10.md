---
title: "MySql on Ubuntu 9.10"
date: 2010-01-21
forum: General Help
---

### Post by lang79james on 2010-01-21
History:
I was using Mint Linux 6 as a main server that host my shared files, MySql, and a VM that was my websver. My VM that host my websever and my other computer both had PHP installed where it would connect to my main sever for databases.

Issue:

Now with Ubuntu 9.10 I can only connect to the database if I am locally connect and using localhost for the server and not the IP address. I get the error message of [HTML]Warning: mysqli_connect() [function.mysqli-connect]: (HY000/2003):
Can't connect to MySQL server on '172.23.50.105' (111) in
/var/www/feedback.php on line 45
Error connecting to MySQL server.[/HTML]

What I have done:

1)Searched google - found out it an network issue connecting to 
MySql over the network

2)Found out what port I was using for Mysql using the 
[HTML]netstat -an | grep -i mysql[/HTML]
unix  2      [ ACC ]     STREAM     LISTENING     5838     /var/run/mysqld/mysqld.sock

3) open that port up along with 3306
change my code to use the IP addess plus the port number IE
192.168.1.23:5838 in the code and still will not connect 

4) edit the my.cnf file so the IP address is binded to computer IP Address and restarted Mysql but it failed to shut down. 

5) Posted to this forum for help

6) Wait for some one that knows more on how to do this for help.

---

### Post by lang79james on 2010-01-21
Ok well an update. I was thinking about the MySql failing to shut down when I restarted it and restarted my computer and it works now.

---

