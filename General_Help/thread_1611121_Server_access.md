---
title: "Server access"
date: 2010-11-01
forum: General Help
---

### Post by Phildough on 2010-11-01
I've set up a really ultra-basic web server with a dyndns account and an old computer lyin' around the apartment. 

I can access (view) the web page from my browser whenever I'm on the local network in my apartment, but cannot seem to when I am anywhere else. I access it locally by using its domain name, which is associated with the router's IP address and then forwarded to the static local IP of the server itself, so I don't see why there is even possibly a difference between trying to access it locally and accessing it globally via its domain name. 

I can access the server via ssh and ftp no matter where I am, so it does not make sense to me why I can't simply view the web page. 

Google chrome returns the error: 
Oops! Google Chrome could not connect to ****.dyndns.tv 

Any help would be appreciated! :)

---

### Post by tornadof3 on 2010-11-01
Your ISP may block port 80? If you are confident that port 80 is open on your router and server and is being correctly forwarded by the router, try [www.canyouseeme.org](www.canyouseeme.org) to check whether your ISP is blocking.

---

