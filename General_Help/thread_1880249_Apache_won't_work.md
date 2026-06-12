---
title: "Apache won't work"
date: 2011-11-13
forum: General Help
---

### Post by choallin on 2011-11-13
Hi guys!

Recently I've switch back to Ubuntu (11.10) after a short time using Windows 7.
So, I have installed Apache 2.2 and some other stuff I need to work. At the beginning everything was fine, but now I have noticed, that I can not get access to any of my files in the var/www directory. At least not in my browser... . I always get the message:
403: Forbidden
You don't have permission to access / on this server.
Apache/2.2.20 (Ubuntu) Server at localhost Port 80

To solve this, I allowed everyone full access (i.e. 0777) On my developing machine, this is no problem. But I'm interested how to configure it right to see the content and not allow everyone everything. Any suggestions?

---

### Post by Lars Noodén on 2011-11-13
> **choallin said:**
> 
To solve this, I allowed everyone full access (i.e. 0777) On my developing machine, this is no problem. But I'm interested how to configure it right to see the content and not allow everyone everything. Any suggestions?


That gives write access even to the web server, any scripts it might run and potentially any guests that can find a hole in your scripts.  (If you are plugged into the net, people are looking for holes.)  You can change it back like this:

```

sudo find /var/www -type d -exec chmod u=rwx,g=rx,o=rx {} \;
sudo find /var/www -type f -exec chmod u=rw,g=r,o=r {} \;

```

IF you are the only user of the development machine then you can simply chown /var/www and its contents to be owned by your account.  If you are sharing write access among a group of developers, then additional steps are needed.

---

### Post by linuxwin2 on 2011-11-14
Apache use www-data as user and group.
Change the owner of /var/www to www-data
```
$sudo chown www-data.www-data -R /var/www/

```

---

### Post by Lars Noodén on 2011-11-14
> **linuxwin2 said:**
> Apache use www-data as user and group.
Change the owner of /var/www to www-data
```
$sudo chown www-data.www-data -R /var/www/

```

Please don't do that.  That gives the web server write access to the web site, and that is something which is dangerous.  Read access is all that is needed or desired for serving web pages.

---

