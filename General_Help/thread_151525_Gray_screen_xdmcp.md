---
title: "Gray screen xdmcp"
date: 2006-03-28
forum: General Help
---

### Post by ento on 2006-03-28
Hi
When an client connects to the server the login screen does not appears.
I will only have a gray screen.
When I'm looking in the ltspcfg the xdmcp service is not installed.

I have enabled xdmcp in gdm.conf, the service is runing and i can login local.

How do i fix it?

/stefan

---

### Post by ento on 2006-03-28
The problem was that the server adress in /var/opt/ltsp/i386/etc/ltsp.conf was wrong.

---

