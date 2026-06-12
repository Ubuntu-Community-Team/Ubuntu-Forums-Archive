---
title: "connect using xdmcp - from outside"
date: 2009-08-19
forum: General Help
---

### Post by soodvarun on 2009-08-19
Hi,
 I am using XLaunch to connect to my linux box in my home network. 

I would like to do the same when I am outside the network but doesnt work.

I have the following ports forwarded.

UDP     177
TCP     177
TCP     6000
TCP     35091
TCP     16001
TCP     6000-6005

I am not a great fan of VNC. So Pls help me work this out.

---

### Post by mjwalfredo on 2009-08-19
Check out FreeNX.  [https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

XDMCP is okay over the LAN but if you want to connect from the Internet, FreeNX not only performs better, but your credentials, and even the session if you want, are encrypted which makes it much safer.

The other option is to use SSH port forwarding for XDMCP.

---

### Post by soodvarun on 2009-08-20
Thanks for your reply.
I will check it out over the weekend and let you know how it went. 

Thanks

> **mjwalfredo said:**
> Check out FreeNX.  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

XDMCP is okay over the LAN but if you want to connect from the Internet, FreeNX not only performs better, but your credentials, and even the session if you want, are encrypted which makes it much safer.

The other option is to use SSH port forwarding for XDMCP.

---

