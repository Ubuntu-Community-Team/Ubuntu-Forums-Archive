---
title: "Can't bind to ports"
date: 2006-05-18
forum: General Help
---

### Post by cadr on 2006-05-18
Hi, i have a problem with server processes binding to ports. If i try to start up a webserver on my local machine (say, the turbogears test server), the process can't bind to a port. Any idea what might be causing this? I assume I must have my localhost entry set up incorrectly in some way, so that binding a port on localhost translates into binding a port on a remote machine where the process can't get permission, but I can't work out exactly what's going on.

Thanks,
Alex

---

### Post by infoburner on 2006-05-18
its probably your local permissions. see, webservers serve on port 80, the http port, but the first 1000 ports are protected. just try to start you webserver with sudo.


for example :
sudo lighttpd

---

### Post by Slim Odds on 2006-05-18
[QUOTE=infoburner]its probably your local permissions. see, webservers serve on port 80, the http port, but the first 1000 ports are protected. just try to start you webserver with sudo.
[/QUOTE]

Yes, it's actually ports below 1024 that are reserved.

He proabaly just needs sudo.

---

