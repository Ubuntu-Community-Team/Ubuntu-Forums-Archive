---
title: "MySQL and MySQL Administrator"
date: 2010-08-13
forum: General Help
---

### Post by zombie_ on 2010-08-13
Hello everyone, 

I got an Ubuntu server and I'm using MySQL on it. I could create a database. Now I would like to access the database via MySQL Administrator. MySQL Administrator asks me about the server host name and I dont know how to specify that. 

Thanks in advance,

---

### Post by DaithiF on 2010-08-13
localhost

---

### Post by zombie_ on 2010-08-13
> **DaithiF said:**
> localhost
How this could be?. 
Im using MySQL on my operating system (Ubuntu) and the database that I created is inside the ubuntu remote server. 

I would be glad if you could help, 

Thanks in advance,

---

### Post by indytim on 2010-08-13
As DaithiF mentioned, the **default** server name is "localhost".

-IndyTim  / DataMan

---

### Post by zombie_ on 2010-08-13
> **indytim said:**
> As DaithiF mentioned, the **default** server name is "localhost".

-IndyTim  / DataMan
Default servername is localhost but its not enough to connect a remote ubuntu server. 

I got the remote server name, lets call it remoteserver and the database that I create in the database of the remote server myremoteDB. 
Now my question is how I can connect to the database remotely. 

Thanks in advance for the help,

---

### Post by DaithiF on 2010-08-13
Hi, you hadn't mentioned in your first post that it was a remote server, so I assumed you were running mysql admin on the same machine as the database.

Do you know the IP address of the server?  You can use that as an alternative to server name.

---

### Post by zombie_ on 2010-08-13
> **DaithiF said:**
> Hi, you hadn't mentioned in your first post that it was a remote server, so I assumed you were running mysql admin on the same machine as the database.

Do you know the IP address of the server?  You can use that as an alternative to server name.
No I dont have the IP. I just got the server name and the name of the database that I created. And would like to connect to the database with MySQL administrator.

Thanks,

---

### Post by DaithiF on 2010-08-13
are you able to ping the server using its name?
ping your-server-name

if so, then you can give mysqladministrator that name

---

### Post by zombie_ on 2010-08-18
> **DaithiF said:**
> are you able to ping the server using its name?
ping your-server-name

if so, then you can give mysqladministrator that name
The this is the database is created inside the muysql. mysql is on my ubuntu server. I want to access the database via my operating system not on the server. 
I could connect to the server via ssh and then do the mysql -u ... -p thing. But I wanted to use a software with GUI for documenting purposes. The software I got is "MySQL Administrator". So Im confused how to use to to conncet the mentioned database. 

Thanks in advance,

---

### Post by DaithiF on 2010-08-18
i understand all that.  you have a ubuntu server running mysql, and that mysql has a number of databases.  you want to connect to a particular database from a different machine, using some client software, Mysqladministrator.

The point I am trying to make is that the client software running on your desktop|laptop|whatever machine needs to know what machine on the network is hosting the mysql instance.  So you need to give it a server address, that server address can either be its IP address, or its server name if you have dns and/or 'hosts' file entries.  You mentioned ssh, ok, when connecting to the server by ssh, what address do you use?  That same address should work for connecting a mysql client.

---

### Post by bilkay on 2010-08-18
My desktop name is "Saturn".

In /etc/hosts.allow is the line:
ALL: 192.168.2.0/24

Installed mysql-server on Saturn, created databases.

Commands issued from laptop:
```
$ mysql -h Saturn
ERROR 2003 (HY000): Can't connect to MySQL server on 'Saturn' (111)

$ mysql -h localhost@Saturn
ERROR 2005 (HY000): Unknown MySQL server host 'localhost@Saturn' (1)
```

---

### Post by DaithiF on 2010-08-18
please post output of:
```
ping -c 4 Saturn

```-- EDIT --
nevermind.  I just wanted to make sure that 'Saturn' is indeed resolvable on your network.  From the error msg i can infer that is.  So the problem is most likely that your mysql server config is set up to only listen for connections on the local address (ie. from that same machine).  Edit /etc/mysql/my.cnf find the line that starts with bind-address, and comment it out by prepending a # character.

then restart mysql on the server 
sudo service mysql restart

---

### Post by bilkay on 2010-08-18
> **DaithiF said:**
> please post output of:
```
ping -c 4 Saturn

```-- EDIT --
nevermind.  I just wanted to make sure that 'Saturn' is indeed resolvable on your network.  From the error msg i can infer that is.  So the problem is most likely that your mysql server config is set up to only listen for connections on the local address (ie. from that same machine).  Edit /etc/mysql/my.cnf find the line that starts with bind-address, and comment it out by prepending a # character.

then restart mysql on the server 
sudo service mysql restart
OK, we're making progress:
```
$ mysql -h Saturn
ERROR 1130 (HY000): Host 'Laptop' is not allowed to connect to this MySQL server
```
After changing field Host to 'Laptop' in table user where field User = ${USER}, I can gain access.

Added another user record for User = ${USER} with Host = 'localhost' and can now access databases from either Saturn or Laptop.

Thanks! I'm fine and I hope zombie_ is too.

---

### Post by curiousapprentice on 2012-04-30
[IMG]http://i46.tinypic.com/necdiq.png[/IMG]

---

### Post by curiousapprentice on 2012-04-30
Install LAMPP and then use MySQL Admin.

---

