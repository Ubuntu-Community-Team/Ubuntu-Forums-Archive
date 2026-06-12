---
title: "how do I uninstall apache2?"
date: 2009-12-22
forum: General Help
---

### Post by ezkim0x on 2009-12-22
I had previously installed mysql and apache2 trying to setup a website.. and then ended up installing xampp. but it can't have apache2 or mysql running while xampp is to work correctly. I got mysql uninstalled correctly. but I still can't figure out how to get apache2 uninstalled. so everytime I restart I have to do this process before xampp will work properly.

```
admin@ks366522:~$ sudo /opt/lampp/lampp start
[sudo] password for admin: 
Starting XAMPP for Linux 1.7.2...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
admin@ks366522:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                           [ OK ] 
admin@ks366522:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.2...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.

```

I tried the following to uninstall apache.. but didn't seem to work.

sudo apt-get remove apache2
sudo aptitude remove apache2

---

### Post by lewisforlife on 2009-12-22
Apache2 is a meta package, this makes it easy to install with an apt-get install apache2, but it is made of of other packages.  Try removing the following packages.

apache2-mpm-event
apache2-mpm-itk
apache2-mpm-prefork
apache2-mpm-worker


I came up with these by doing:

```
apt-cache show apache2 | grep Depends
```

---

