---
title: "Apache on port 8010"
date: 2009-09-14
forum: General Help
---

### Post by loveguitarncomp on 2009-09-14
Hi,

I am trying to setup apache 2 on port 8010 in addition to port 80. when I try to access the server with it's ip address and port like below:
[http://192.168.1.8:8010](http://192.168.1.8:8010) I can't get the page and I get an error 404 not found. However on port 80 it works. Strange thing is that I can telnet to port 8010 and it get's connected. Pls advise what could be wrong. I just downloaded and installed the latest version of Ubuntu Server Edition.

Regards,
D

---

### Post by KiLaHuRtZ on 2009-09-14
You have to tell Apache to listen on port 8010.  Add the following line to '/etc/apache2/ports.conf'.

```
Listen 8010
```

After that a restart will be required.

```
sudo /etc/init.d/apache2 restart
```

---

### Post by loveguitarncomp on 2009-09-14
Hi,

Sorry I forgot to mention that it's already added and I restarted the server too. But still I can't access it.

Regards,
D

---

### Post by P4man on 2009-09-14
If you get a 404, then apache is working on that port, just not configured to serve the right site.
Have a look here:
[http://httpd.apache.org/docs/1.3/bind.html](http://httpd.apache.org/docs/1.3/bind.html)

---

### Post by BUSHYBOB on 2009-09-14
Try changing this

[http://192.168.1.8:8010]("http://192.168.1.8:8010/")

to this

[http://192.168.1.8:8010]("http://192.168.1.8:8010/")/

---

### Post by loveguitarncomp on 2009-09-14
> **P4man said:**
> If you get a 404, then apache is working on that port, just not configured to serve the right site.
Have a look here:
[http://httpd.apache.org/docs/1.3/bind.html](http://httpd.apache.org/docs/1.3/bind.html)


Hi,

When I type [http://192.168.1.8](http://192.168.1.8), the page is served but when I type [http://192.168.1.8:8010](http://192.168.1.8:8010) I don't get a page at all and through lynx browser, it returns 404.

Do you think it could be because of Virtual Hosts? How do I disable it as I really don't need Virtual Hosts.

---

### Post by loveguitarncomp on 2009-09-14
I found the solution. It was the virtual host setting:
I edited the below file. It was:
/etc/apache2/sites-enabled/000-default
<VirtualHost *:80>
I made it
<VirtualHost *:*>


Thanks for your help guys.

---

