---
title: "Getting apache2 virtual hosts to run on my local machine"
date: 2012-09-02
forum: General Help
---

### Post by ajlee on 2012-09-02
I am trying to setup a local webserver on my laptop.

I'm getting this on startup of apache2:

(9Address already in use: make_sock: could not bind to address 0.0.0.0:80


It doesn't look to me like anything is using port 80:


$ lsof -i :80
COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME
chrome 2058 andrew 66u IPv4 19499 0t0 TCP 192.168.1.105:50386->173.192.42.178-static.reverse.softlayer.com:www (ESTABLISHED)
chrome 2058 andrew 101u IPv4 17700 0t0 TCP 192.168.1.105:47255->lga15s34-in-f2.1e100.net:www (CLOSE_WAIT)
chrome 2058 andrew 104u IPv4 17702 0t0 TCP 192.168.1.105:39086->vb-in-f106.1e100.net:www (ESTABLISHED)

$ sudo netstat -lnp | grep ':80 '

Returns nothing....

Any ideas of what to check? I'm running 11.10. Thanks!

I should also say that the default site works - I am trying to setup virtual hosts.

---

### Post by Lars Noodén on 2012-09-02
What about [font=Courier New]/etc/init.d/apache2 status[/font]?  That should give at least one PID.

What kind of virtual hosts are you running?  Name-based or port-based?

---

### Post by ajlee on 2012-09-02
Nevermind, found it.  I had parms defined in both httpd.conf and apache2.conf and they were conflicting.  Removed everything from httpd.conf and it fixed my issue.  Thanks!

---

### Post by Lars Noodén on 2012-09-02
Glad it works.  

http.conf confuses just about everyone the first time they set up Apache2.  I'm not sure why was kept around.  It seems to be gone from 12.04

---

