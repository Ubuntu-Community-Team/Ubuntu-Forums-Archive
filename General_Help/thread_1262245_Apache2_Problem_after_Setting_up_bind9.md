---
title: "Apache2 Problem after Setting up bind9"
date: 2009-09-09
forum: General Help
---

### Post by rublind on 2009-09-09
Hello,

I finally got bind9 all configured and working, and next thing I know, apache died!

I tried checking the log, but all I get is ```
Unable to open logs
```

I also tried running ```
sudo apache2ctl restart
``` and I got the following message:
```
httpd not running, trying to start
``` but it doesn't start... running it not as root gives the following:
```
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open log
```s

I don't know what to do. :(

Please help! 

Thank you,
 -- Julian

---

### Post by ALnot on 2009-09-11
try /etc/init.d/apache2 reload
or
try /etc/init.d/apache2 restart

---

### Post by rublind on 2009-09-11
ALnot,

I did try those.

I found the problem, but forgot to post the solution.

In one of my vhost files (in sites-available) I made an error when typing the path for the log, so that's why it was "unable to open log."

Stupid reason to fail if you ask me...

But thanks for the help anyway! :)

---

