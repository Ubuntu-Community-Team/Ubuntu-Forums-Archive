---
title: "Can't connect to my MySQL DB on my Ubuntu Server from a remote machine"
date: 2012-03-26
forum: General Help
---

### Post by TMcKSmith on 2012-03-26
I know I must be missing something easy here so I was hoping someone could point me in the right direction. 

I have a remote Ubuntu Server running MySQL that I've been using for years now. I have a forum that currently uses it with no issues whatsoever. I login quite often to the phpMyAdmin page located at [http://www.mywebsite.com/phpmyadmin](http://www.mywebsite.com/phpmyadmin) 

I just installed MySQL Workbench and attempted to connect to the database from my local laptop. I provided the following credentials: 

hostname: mywebsite.com 
port: 3306 (I made sure my router is forwarding this port using both TCP/UDP) 
username: myusername (this is the user I use to connect to phpMyAdmin which has ALL privileges) 


Default Schema I left blank 


Anyway, it says it's unable to connect.  Is there something I'm missing? Any help would be appreciated.

---

### Post by gsgleason on 2012-03-26
[http://lmgtfy.com/?q=mysql+allow+remote+connections](http://lmgtfy.com/?q=mysql+allow+remote+connections)

First result is what I used and it worked well.

---

### Post by TeoBigusGeekus on 2012-03-26
MySQL Workbench is a worthless piece of software. Its buggy parts are more than its functioning ones; don't waste your time with it.

---

### Post by idoitprone on 2012-03-26
> **TeoBigusGeekus said:**
> MySQL Workbench is a worthless piece of software. Its buggy parts are more than its functioning ones; don't waste your time with it.

really? i just use it to make diagrams. I never knew that program is that bad

---

### Post by gsgleason on 2012-03-28
Fortunately that is not relevant.  If it serves your purpose, then use it.

---

### Post by SeijiSensei on 2012-03-28
Do you have an entry for yourself as 'user'@'hostname' on the MySQL server with the hostname of your client machine?  My bet is you have a 'user'@'localhost' entry, which will not [authenticate]("http://dev.mysql.com/doc/refman/5.5/en/connection-access.html") you if you log in from any other machine.  Try creating a 'username'@'%' account which enables logins from any host, or create a specific one for your remote client if you're concerned that the '%' hostname is too insecure.

Are you sure port 3306 is open?  Check to see if you get a connection reply using "telnet servername 3306" from your client.

Is the port on the server [bound]("http://dev.mysql.com/doc/refman/5.5/en/server-options.html#option_mysqld_bind-address") to just the localhost (127.0.0.1) interface?  That's the Ubuntu default for security reasons, I believe.

---

