---
title: "what command shows boot output?"
date: 2012-02-08
forum: General Help
---

### Post by daweefolk on 2012-02-08
I searched the forums (probably not the right terms) but I can't find what I'd type at the command line to show me the output while linux boots. I want to see what services are starting, so I can remove ones I don't use.

---

### Post by wyliecoyoteuk on 2012-02-08
dmesg
 will give you a list of bootup messages,
ps
 will show you all currently running processes.
service --status-all 
will show you all running services.

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

There are also various GUI solutions, but I mainly use Webmin on my servers.
[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by daweefolk on 2012-02-08
thank you! dmesg is exactly what i was trying to remember

---

