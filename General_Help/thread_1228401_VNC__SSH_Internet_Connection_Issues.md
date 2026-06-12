---
title: "VNC / SSH Internet Connection Issues"
date: 2009-07-31
forum: General Help
---

### Post by eymorais on 2009-07-31
Hi Everyone,
 
This one is incredibly weird and unexplainable.
 
Currently have a Ubuntu 8.04 Lamp server with SSH and VNC Services active. I can connect to both the VNC and SSH Service on my local network but can't access them via the Internet. I can access my Apache and FTP server via my DynDNS Based domains but I can't access bot VNC and SSH services. They both return a "network connection timed out". 
 
A screen shot of my router settings is attached.
 
 
Any suggestions would greatly be appreciated.

---

### Post by Brandon Williams on 2009-08-02
Are you sure that VNC is using port 5900? My VNC session is listening on 5901 and 6001. And what is the port 77 mapping for? ssh uses port 22, unless you've reconfigured it.

Double check the ports, reconfigure the router, and try again.

---

### Post by eymorais on 2009-08-04
I've got my SSH server on port 77 instead of 22.
 
I can connect to my VNC server via my lan on port 5900 thus the reason why I have my router forwarded on port 5900.

---

### Post by eymorais on 2009-09-11
Hi Everyone, got my VNC to work. Was a proxy issue on the network I was connect from.

Now to get my SSH service to work, but that will be for a different tread now.

---

