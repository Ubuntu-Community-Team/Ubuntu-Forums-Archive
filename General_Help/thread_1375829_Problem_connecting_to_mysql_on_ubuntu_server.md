---
title: "Problem connecting to mysql on ubuntu server"
date: 2010-01-08
forum: General Help
---

### Post by omsoni on 2010-01-08
I am new to Ubuntu Server. 
Just installed LAMP (on Ubuntu) on new Server I bought. 
I want to connect to mysql database on this server from my laptop (running Windows Vista) using mysql administrator. 

I can ping the server from laptop successfully. 
Mysql database is started and I am able to connect to it from command line on server.
When I try to connect to database from my laptop using Mysql Administrator it fails to connect.
 
Please help me get started on this. 
Thanks in advance.

---

### Post by DaithiF on 2010-01-08
edit /etc/mysql/my.cnf and comment out the bind-address = 127.0.0.1  line by prepending #.

then restart mysql...
sudo /etc/init.d/mysql restart

---

### Post by ProfessorSr on 2010-01-08
I am having a similar problem. I can connect using the command line and administrator, web pages can't
 
Any suggestions anyone.
Oh I have commented out the bind-address
 
Just curious, Omsoni. Did you set up port forwarding on your router for port 3306 to the ip address of your ubuntu machine

---

### Post by omsoni on 2010-01-09
No I did not setup the port forwarding on my router.
How do I do it ?

OK I went to admin page of my motorola router->Networking->Port Trigger
then I setup 3306 as my outgoing and incoming port.

Is it correct ?

---

### Post by ProfessorSr on 2010-01-09
give me model number of router and I will be able to give you more info
 
by chance when you setup the port 3306 did you have to specify an ip address

---

### Post by omsoni on 2010-01-09
[ProfessorSr]("http://ubuntuforums.org/member.php?u=993614"),

No I did not specify the ip address. But I manage to connect to mysql on server from my laptop.

Are you still having this issue ?

---

### Post by ProfessorSr on 2010-01-09
my issue is a little more complicated. I am running ubuntu with mysql on a vmware server. The cool part is that the computer that is running this setup is in Tennessee. I use a remote desktop to control it from Arizona.
 
But anyways. I can connect to the MySQL server on the vmware ubuntu setup using the mysql GUI tools on my local machine here in AZ just by entering the ip address of the router in TN and username and password. All this works fine (had to do some tweaking to make this work).
 
But when using the same ip address that I use for the MySQL Admin GUI I can not connect. Any ideas.

---

### Post by omsoni on 2010-01-09
Not sure,

Seems like anytime you connect to mysql database from a different host you have to setup the access privileges.

I ran this command to setup the privileges for my username and laptop:

   Grant all privileges on *.* to <UserName>@<hostname> identified by ‘password’


Good Luck

---

