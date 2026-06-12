---
title: "Unison Cron Tab"
date: 2011-03-19
forum: General Help
---

### Post by dymonik on 2011-03-19
Hello, 

I am using CentOS 5, which i hope it's okay that i am posting here.  

And what i really need is someone to make me a complete idiots guide for setting up a cron to do the following

i have 2 load balanced webservers.....

server1.mydomain.com
server2.mydomain.com

and i need a Cron that will automatically sync    /var/www/html

The command i have used that works is

~ cd /var/www
~ unison html [ftp://my.ip.address.here//var/www/](ftp://my.ip.address.here//var/www/)

but i am then prompted for a password. and must enter it.

So what i need is an idiots guide, like word for word on what to do to set it up for a cron tab to do this every 5 minutes, as well as what is needed to do to add the auth key so that it works without prompting for password.  but i need it to be very secure. so that only server1 is able to do so.

and my knowledge of linux is none. so i really need detailed explanations of everything, and would greatly appreciate it :)

---

### Post by dymonik on 2011-03-19
Correction....   ssh* not FTP

---

### Post by dymonik on 2011-03-21
bump.  i need a miracle.

---

