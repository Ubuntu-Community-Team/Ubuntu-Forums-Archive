---
title: "is the /etc/hosts file related to subdomains?"
date: 2010-02-16
forum: General Help
---

### Post by programming.name on 2010-02-16
Hi, I am trying to add subdomains on ubuntu 9.10 desktop edition and and I am not sure whether I need to add some info.(such as 127.0.0.1          sub1.example.com and so on) to the /etc/hosts file like the windows' windows/system32/drivers/etc/hosts file. 

I used to use the wamp-server(on Windows 7), I needed to edit 3 files, httpd.conf, httpd-vhosts.conf and hosts. And almost every edit is made in the httpd-vhosts.conf file on wamp-server.

Could anyone help me which files should be edited? or what else should be done that  I didn't mention? 

Thanks.

p.s. I got port forwarded, and DNS ready.

---

### Post by ttoilleb on 2010-02-16
Are you planning on using 2 PCs?  1. Windows with WAMPP running and 2. Ubuntu to access it?  The answer makes a difference.

In short the /etc/hosts and the c:/windows/system32/drivers/etc/hosts perform identical functions in identical ways.  If you needed to put in a pointer to a (sub)domain on windows, you will also need to do so on Ubuntu.  However, if you are running the WAMPP stack on windows, the ip you enter on Ubuntu must to the IP of your windows box.  IE: If your windows box is 192.168.1.24 and the subdomain you want to use is "testing.localdomain.com".  

On the ubuntu machine you would need a line in /etc/hosts - 
           192.168.1.24  testing.localdomain.com.

On the windows box you would need a line in c:/windows/system32/drivers/etc/hosts - 
           127.0.0.1  testing.localdomain.com

---

