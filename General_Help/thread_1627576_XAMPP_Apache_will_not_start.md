---
title: "XAMPP Apache will not start"
date: 2010-11-21
forum: General Help
---

### Post by stepheny on 2010-11-21
I have a PC running 64-bit Ubuntu 10.04 on which I want to install XAMPP. I have used the howto [here]("http://ubuntuforums.org/showthread.php?t=223410")  but whatever I do I cannot get the Apache server to run. When I input the command ```
sudo /opt/lampp/lampp start
``` everything seems to work and there are no warnings but on directing a browser to localhost there is an "unable to connect" message. On typing ```
sudo /opt/lampp/lampp stop
``` I get the following message which shows that Apache was never started:
```
Stopping XAMPP for Linux 1.5.3a...
XAMPP: XAMPP-Apache is not running.
XAMPP: Stopping MySQL...
XAMPP: Stopping ProFTPD...
XAMPP stopped.
```

At first I simply stopped the other Apache server but eventually I  completely removed any other Apache instances with the command ```
apt-get remove --purge apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert
``` but still the XAMPP Apache will not start.

The only errors in the ```
/opt/lampp/logs/error.log
``` are:
 
```
[Sun Nov 21 20:42:02 2010] [notice] suEXEC mechanism enabled (wrapper: /opt/lampp/bin/suexec)
[Sun Nov 21 20:42:02 2010] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sun Nov 21 20:42:02 2010] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
```

Can anyone offer any advice on why the XAMPP Apache will not start?

---

