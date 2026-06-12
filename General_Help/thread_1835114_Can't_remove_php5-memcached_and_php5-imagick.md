---
title: "Can't remove php5-memcached and php5-imagick"
date: 2011-08-28
forum: General Help
---

### Post by makescents on 2011-08-28
Hello,

I've been attempting to run php through my nginx server so I installed the following:

```
sudo apt-get install php5-cli php5-common php5-suhosin
```

Then:

```
sudo apt-get install php5-cgi php5-fpm php5-pgsql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-recode php5-snmp php5-tidy php5-min php5-ps php5-xmlrpc php5-xsl
```

I wanted to run through CGI and I'd read that I didn't need a wrapper so I ignored php5-fpm and ran.

```
php-cgi -b 127.0.0.1:9000
```

But it never worked, just left me hanging so I ^C  out.

I then tried php5-fpm but php5-ming and php5-ps stopped that from running.

I apt-get removed those two modules and then my php.ini complains that they are missing. I believe this was because I didn't purge, can somebody confirm that?

So I decide to do a refresh of everything and run apt-get purge on everything.

This results in:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  php5-imagick php5-memcache
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 705 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 33846 files and directories currently installed.)
Removing php5-imagick ...
sed: can't read /etc/php5/conf.d/imagick.ini: No such file or directory
dpkg: error processing php5-imagick (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing php5-memcache ...
sed: can't read /etc/php5/conf.d/memcache.ini: No such file or directory
dpkg: error processing php5-memcache (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 php5-imagick
 php5-memcache
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How does one go about removing these broken packages?

---

### Post by makescents on 2011-08-28
Ok to solve this:

```
cd /etc/php5/conf.d/

sudo touch memcache.ini
sudo touch imagick.ini

```

Then run:

```
sudo dpkg --purge --force-all php5-imagick php5-memcache
```

Packages be gone.

---

