---
title: "apache/php, serving php files for download instead of executing them"
date: 2009-12-21
forum: General Help
---

### Post by kingster80 on 2009-12-21
I have seen a couple of threads like this, but they were not very helpful.

My problem is: When I try to execute my php files in my browser from my ubuntu hardy server, the browser offers to download the files instead of the server proccessing them.
whats worse the file it allows me to download is not the proccessed output but the "code" file. these files could have database name, password and what not. Not so good!!!

For some reason though, my webmin works. (probably because its https and not http)

First off all, it has worked before. I haven't  used it for quite a while, but resently i updated webmin to version 1.500 (dont know if this is the reason for my problems), but I just noticed problems after the update.

I have tried reinstalling apache and php, but to no avail. Any ideas???


[SOLVED]
I got an error when restarting apache:
"namevirtualhost *:0 has no virtualhosts"
 After deleting the "NameVirtualHost *" line in "/etc/apache2/sites-available/default", and then clearing the browser cache, it all worked!!

---

### Post by kbates666 on 2009-12-22
I have the exactly the same problem...I have tried everything I can think of. I tried to do the recommended fix above but to no aval. Any Ideas?

---

### Post by bodhi.zazen on 2009-12-22
first, install libapache2-mod-php5

```
sudo apt-get install libapache2-mod-php5
```Then enable it

```
sudo a2enmod php5
```

Restart paache

```
sudo service apache2 restart
```

Clear your cache on your browser, and re-load the page.

---

### Post by kbates666 on 2010-01-07
That worked perfectly thanks!

Apparently the package libapache2-mod-php5 was removed for some reason. A quick reinstall and restart did the trick.

---

### Post by Atroban on 2012-08-20
Thanks!

---

