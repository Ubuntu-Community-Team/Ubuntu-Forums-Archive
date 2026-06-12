---
title: "localhost &quot;Failed to Connect&quot; (worked previously)"
date: 2010-02-03
forum: General Help
---

### Post by proten on 2010-02-03
Hi,
I am pretty new to linux so please forgive my ignorance in advance. I installed required updates on my linux installation (ubuntu 9.4)  I am now unable to access my localhost, and get the following message from my browser:
Failed to Connect
Firefox can't establish a connection to the server at localhost.
Though the site seems valid, the browser was unable to establish a connection.

I checked my hosts file which has the following information:
127.0.0.1    localhost
127.0.1.1    ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I dont even know where to start...
Please help!

---

### Post by jken146 on 2010-02-03
What were you expecting to see?  Are you running a web server (e.g. Apache)?

---

### Post by proten on 2010-02-03
Yes I have apache (xampp) installed.  The following are the localhost url's that I've tried before and they all worked previously.

localhost
localhost/phpmyadmin
localhost/drupal

Thanks!

---

### Post by gmargo on 2010-02-03
Sounds like your web server is not running. From a command line you can use "ps" to look for the apache process.  And you can use "netstat" to see if any process is currently listening on port 80 (the HTTP port).  Here's what it looks like on my machine:

```

$ ps -efw | grep apache
www-data  3543 11365  0 Feb02 ?        00:00:00 /usr/sbin/apache2 -k start
root     11365     1  0 Jan24 ?        00:00:18 /usr/sbin/apache2 -k start
gmargo   12824 11735  0 10:11 pts/9    00:00:00 grep apache
www-data 17845 11365  0 Jan31 ?        00:00:00 /usr/sbin/apache2 -k start
(additional similar lines deleted ...)

$ netstat -an | grep :80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     

```

---

### Post by proten on 2010-02-03
If it is not running, what do I need to do to start it?

---

### Post by proten on 2010-02-03
This is strange
sudo /opt/lampp/bin/apachectl start 

and now my localhost/drupal page works.

however when i access localhost/myphpadmin site, it asks me to download main.php??

Any ideas?

---

### Post by proten on 2010-02-03
Got it now, I needed to start lampp, not just apache
Solution: sudo /opt/lampp/lampp start
started xampp and I'm good now.

Thanks!

---

