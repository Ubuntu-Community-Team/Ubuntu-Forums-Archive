---
title: "Connecting to MySQL from another pc"
date: 2009-11-05
forum: General Help
---

### Post by thescubadude on 2009-11-05
Ok, so I have setup a LAMP server with phpmyadmin on my UBUNTU machine.

I can connect through my two windows pcs to my virtual hosts, I can connect to MySQL through phpmyadmin but I would like to connect through MySQL QueryBrowser & MySQL Adminstrator. phpMyAdmin is great but coming from a microsoft background I find the QueryBrowser and Administrator easier to work with.

When I try to connect using the ip of my server computer, as I can to connect to phpmyadmin, I get the following error: mysql error no. 2003 (can't connect to mysql server on 192.168.1.8(10061).

If I then use the ping button it does get a response???

What is the default port for mysql on Ubuntu? 

How do I check which port MySQL is listening to? 

How can I connect? 

Is there something I need to setup to allow connections from remote locations/internal network locations?

Thanks in advance for any help.

---

### Post by dchurch24 on 2009-11-05
The port is 3306 - you probably have already done this, but make sure that port is forwarded correctly if connecting through a router. To check the port run:

```

nmap localhost

```

...on the local machine. (if it's not installed: sudo apt-get install nmap).

Other than that, I don't really know as I haven't used the tools you mention - I've either used the PHPMyAdmin or the MySQL command line options.

---

### Post by thescubadude on 2009-11-05
Ok, I have run nmap.

My ubuntu machine, which is acting as the server has the ip address 192.168.1.8.

If I run nmap localhost mysql is on port 3306

If I run nmap 192.168.1.8 on the ubuntu machine then I do not get mysql through nmap. it lists everything else the same just without mysql. 

what can i do to change this so that I can try access mysql on 192.168.1.8 port 3306

---

### Post by breadlord on 2009-11-05
You need to give the user you're connecting with remote privileges. Here's a guide.

[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

---

