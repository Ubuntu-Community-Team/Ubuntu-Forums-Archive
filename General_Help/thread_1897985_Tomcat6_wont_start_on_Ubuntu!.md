---
title: "Tomcat6 wont start on Ubuntu!"
date: 2011-12-20
forum: General Help
---

### Post by renegadeandy on 2011-12-20
Hey guys -when trying to launch Tomcat Server via Eclipse in Ubuntu it fails with :

> Several ports (8005, 8080) required by Tomcat v6.0 Server at localhost are already in use. The server may already be running in another process, or a system process may be using the port. To start this server you will need to stop the other process or change the port number(s).

I then do:

[PHP]lsofandy@andy:~$ lsof -iTCP:8005
andy@andy:~$ lsof -iTCP:8080
andy@andy:~$ lsof -iTCP:80
COMMAND   PID USER   FD   TYPE     DEVICE SIZE/OFF NODE NAME
chrome   2172 andy  109u  IPv4 2375898071      0t0  TCP 192.168.50.102:56834->fa-in-f104.1e100.net:www (ESTABLISHED)
chrome   2172 andy  139u  IPv4 2375923921      0t0  TCP 192.168.50.102:49407->ey-in-f95.1e100.net:www (ESTABLISHED)
^C
andy@andy:~$ lsof -iTCP:800
andy@andy:~$ lsof -iTCP:8005
andy@andy:~$ lsof -iUDP:8005
andy@andy:~$ lsof -iUDP:8080
andy@andy:~$ lsof -iTCP:8005
andy@andy:~$ lsof -iTCP:8005
andy@andy:~$ lsof -iTCP:8080
andy@andy:~$ 


[/PHP]

Which proves nothing is running on 8005 or 8080, so why doesnt this start!?

---

