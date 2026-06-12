---
title: "LAMP with suphp installed"
date: 2010-03-07
forum: General Help
---

### Post by majdi on 2010-03-07
Hi,

Trying to setup a LAMP install with suphp on Ubuntu 8.04. I had the LAMP installed and tested working fine, until I tried installing suphp. 

I followed the following instructions ([http://www.pc-freak.net/blog/installing-suphp-on-debian-lenny-5-04-with-apache-2-2-9-2/]("http://www.pc-freak.net/blog/installing-suphp-on-debian-lenny-5-04-with-apache-2-2-9-2/")) starting with step 2, because I had used Synaptic to install suphp.

Now it seems PHP is not working, apache is running fine. Anyone with a fix? For example, how would I reverse the (a2dismod php5) command, maybe that is a start to get php working again, then I would need to fix suphp.

---

### Post by MinimalBin on 2010-03-07
a2enmode ?

---

### Post by majdi on 2010-03-08
> **MinimalBin said:**
> a2enmode ?

a2enmod is an apache script that enables modules very easily for you (it actually just makes a symlink in /etc/apache2/mods-enabled to a corresponding /etc/apache2/mods-available file),an attempt by debian to atone for their sins.

So, any help fixing my php to work with suphp, I noticed there is no mention of the php.ini file, wouldn't this need some editing for suphp to work?

---

### Post by majdi on 2010-03-11
I have a LAMP setup and running on Ubuntu Desktop 8.04.4 LTS. I have installed the following;

Apache/2.2.8 (Ubuntu)
PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch
Mysql 5.0.51a
libapache2-mod-suphp

I cant get suphp to work. I followed these instructions [http://www.pc-freak.net/blog/installing-suphp-on-debian-lenny-5-04-with-apache-2-2-9-2/](http://www.pc-freak.net/blog/installing-suphp-on-debian-lenny-5-04-with-apache-2-2-9-2/) but then php stopped working, so I reversed step 2 to have it working again.

I used phpinfo() script to check the php settings and I can see mod_suphp listed under Loaded Modules. Also in the PHP setting Server API = Apache 2.0 Handler, but from my search it should show; Server API = CGI if suphp is working.

Anyone has this working on Ubuntu, please help.

---

