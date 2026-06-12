---
title: "MySQL connection"
date: 2006-06-04
forum: General Help
---

### Post by Robgould on 2006-06-04
ok....I have MySQL installed in Dapper.  I also have administrator and query browser installed.  I can connect to localhost and configure the MySQL server with administrator, but I cannot connnect from a remote host.  I added a new user with all shcema rights and anyhost (@%).  I did this with mysql-administrator.

I installed another administrator on a winxp virtual machine with bridged networking.  I turned off the windows firewall to eliminate it.  I can ping the computer, but cannot connect to the MySQL server.  I have tried install firestarter and adding a rule for 3306.  I have tried configuring my router till I can't even remember what the hell I tried.  I don't believe that is the issue though.  I could connect between winxp and CetnOS with not issue.  I just had to configure the firewall on XP and CentOS.  

I have not had ANY luck connecting to MySQL running on Ubuntu.  Can anyone help me?

---

### Post by ZylGadis on 2006-06-04
Sure - it's simple: mysql on ubuntu by default only listens on localhost (127.0.0.1). This means you can't connect from the outside. Check its config file (should be smth like /etc/mysql.conf) for directions on what to do.
Remember that Ubuntu by default is unpenetrable from the outside, and if you wish to make it less secure, you have to do it by yourself :)

---

### Post by palermi on 2006-06-04
i have this problem

palermi:$ **mysqld**
060604 22:56:49  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

and cant access with my root pass :S

**sudo mysql -uroot**
Password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Robgould on 2006-06-05
My thread is being hijacked.  
 
The file turns out to be /etc/mysql/my.cnf
 
I am not sure about everything that is in there.  There is a section about skip-external-locking and and a bind-address to 127.0.0.1 (localhost).
 
I opened the mysql-administrator (had to run as root) and found on the advanced tab of the start-up parameters for mysqld a setting for "bind to IP".  I unchecked that.  It backed up my my.cnf and created a new one with all the stuff about external locking and binding commented out.  
 
I can't try this until tonight, but I thought I would just ask on here if this sounds right.  Thanks for any help.

---

### Post by Ronbo on 2006-06-05
I had the same problem, you have to comment out the line in /etc/mysql/my.cnf that says "bind address    =    127.0.0.1".  But it sounds like you already did that.  Then what i had to do is privileges in mysql to the user to login from the networked machine I wanted to use.  I opened a terminal and logged in to mysql.  Then I issued the command:

mysql> GRANT ALL PRIVILEGES ON *.* TO *'your_username'*y@'%'
           IDENTIFIED BY *'your_pass'* WITH GRANT OPTION;  

But this will grant the user all priviliges, which I am sure is not the reccomended way of doing it,  if you want to limit their permissions:
[http://webdocs.math.univ-rennes1.fr/MySQL/mysql-3.23.52/manual_Adding_users.html]("http://webdocs.math.univ-rennes1.fr/MySQL/mysql-3.23.52/manual_Adding_users.html") 

I then restarted the mysql server and could login from the machine I needed to work from.  I don't know if this will solve your problem, but it sounds kinda like the same problem I was having.  Hope this helps.

---

### Post by Robgould on 2006-06-05
Thanks for all the help....I think that will get me what I need.

---

### Post by Robgould on 2006-06-06
Just to follow-up, that worked perfect.  Thanks everyone for all the help.

---

