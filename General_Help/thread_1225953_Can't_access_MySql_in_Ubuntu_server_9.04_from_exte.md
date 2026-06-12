---
title: "Can't access MySql in Ubuntu server 9.04 from external softwares"
date: 2009-07-29
forum: General Help
---

### Post by ularlaut on 2009-07-29
Hello,

I need an assistance, I can not access MySql Database in my Ubuntu Server 9.04 from MySql Administrator console / software; 
But I can access my MySQL interface from web browser.

I already follow each and every step from the manual book and also from other external resources, but still no solutions.

Anybody can help me with this problem ?

Thank you very much for the kind attentions.

regards.

---

### Post by DaithiF on 2009-07-29
Hi,
Hard to say for sure without more details of what you have done so far, but most likely there are 2 things you'll need to do:
1. Enable mysql access from remote hosts (this is disabled by default).  Note that accessing mysql via browser (e.g. via phpmyadmin) doesn't count as remote access as far as mysql is concerned, since it is the web service you are accessing remotely, but web service is accessing mysql from the local machine.
if you want to enable remote access then do:
```
sudo gedit /etc/mysql/my.cnf

```
find the line like 
bind-address 127.0.0.1
add a # character to the front of it to comment it out
restart mysql:
```
sudo /etc/init.d/mysql restart
```

Secondly, what user are you trying to connect as?  Make sure that user is allowed to connect from either the specific host you are connecting from, or '%' if you want access from any remote machine.  You can do this via the Privileges menu item on phpmyadmin.   
good luck, post back with any problems
d

---

### Post by ularlaut on 2009-07-29
Thank you very much to Daithif for the information's

It works now.

JBU... :)

---

