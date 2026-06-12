---
title: "Port 80 taken by command '18'"
date: 2009-09-06
forum: General Help
---

### Post by kc600 on 2009-09-06
Will investigating why my web site was down, i discovered port 80 was taken by a process with command '18':

```
me@server:~$ sudo /etc/init.d/apache2 start
Starting web server (apache2)...(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
 failed!
me@server:~$ ps ax | grep apache
 2723 pts/1    S+     0:00 grep apache
me@server:~$ ps ax | grep httpd
 2725 pts/1    S+     0:00 grep httpd
me@server:~$ 
me@server:~$ lsof -i tcp:80
me@server:~$ sudo lsof -i tcp:80
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
18      17328 root    4u  IPv6 482908       TCP *:www (LISTEN)
me@server:~$ sudo kill 17328
me@server:~$ sudo /etc/init.d/apache2 start
Starting web server (apache2)....
me@server:~$ 
```

Killing that process worked to fire up apache again.

But can anyone tell me what may have happened?

---

### Post by kc600 on 2009-11-16
Turns out i was infected by an SHv4/SHv5 rootkit. I noticed this only when i tried to upgrade some packages.

Edit: this was informative: [http://www.void.gr/kargig/blog/2009/10/04/epic-fail-from-a-hosting-company-involving-bad-customer-support-and-a-critical-security-issue/](http://www.void.gr/kargig/blog/2009/10/04/epic-fail-from-a-hosting-company-involving-bad-customer-support-and-a-critical-security-issue/)

---

