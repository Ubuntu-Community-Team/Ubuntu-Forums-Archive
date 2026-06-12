---
title: "starting apache"
date: 2009-09-23
forum: General Help
---

### Post by Bensky5012 on 2009-09-23
I've successfully installed apache web server, now how do I start the server?

---

### Post by scragar on 2009-09-23
It's a deamon, so:
```
sudo /etc/init.d/apache2 start
```
And to stop:
```
sudo /etc/init.d/apache2 stop
```
And restart:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by Bensky5012 on 2009-09-23
I'm getting this:
```

sudo: /etc/init.d/apache2: command not found

```

---

### Post by scragar on 2009-09-23
/me grumbles
Stupid punk-***** weird naming convention, naming the package apache2 the folder www and the deamon apache...

Remove the 2 off the code I posted, sorry.

---

### Post by Bensky5012 on 2009-09-23
again:
```

sudo: /etc/init.d/apache: command not found

```

To install I did, configure, then make, then make install.  Is this all I needed to do?

---

### Post by scragar on 2009-09-23
Wait, why did you install it from source?
There's a package of it maintained by ubuntu which comes with updates, doesn't leave me trying to guess the deamon name and let's you install modules without having to recompile apache...
For future ref:```
sudo apt-get install apache2
```Would have been easier.
For now can you do```
ls /etc/init.d
```And let me know what's in that folder, I'm going to guess it's called itself **httpd** rather than apache, since that's the recommended naming convention apache wanted since the upgrade(to avoid problems the install path for web files is now /srv/httpd rather than /var/www which makes no sense to me :p)

---

### Post by Clonito on 2009-09-23
@[Bensky5012]("http://ubuntuforums.org/member.php?u=804348"): You don't need to compile, we have it on official repos.
```

sudo apt-get install apache2

```
But, you should try lighttpd, is easy..fast and does the same job..web server.
```

sudo apt-get install lighttpd

```
and start the web server:
```

sudo /etc/init.d/lighttpd start

```
maybe, just maybe after installation, the server started by default.

---

### Post by Bensky5012 on 2009-09-23
I installed lighttpd and its working fine now, thanks.  How would I go about uninstalling apache?

---

### Post by scragar on 2009-09-23
```
sudo make uninstall
```
In the source directory, like how you installed it in the first place.

---

### Post by Bensky5012 on 2009-09-23
Thanks again!

---

### Post by Bensky5012 on 2009-09-23
Where do I stick my html/php files for lighttpd

---

### Post by Clonito on 2009-09-23
> **Bensky5012 said:**
> I installed lighttpd and its working fine now, thanks.  How would I go about uninstalling apache?
You welcome :)

---

