---
title: "Help with Apache Rewrite Cond"
date: 2010-12-13
forum: General Help
---

### Post by chrislynch8 on 2010-12-13
Hi,

I have an internal web application that is accessable internally and externally. I have a DNS record pointing to my application for external access and I have a rewrite rule that forces access over https. TO access this a user uses the url app.domain.com

For internal access the users enter a differnet URL app.our.org - managed by lour internet DNS servers. It is working great, but I want to make it work as follows

I want to just use app.domain.com for both internal and external access, but I want apache2 to know when it is an External Connection to push over https and when its internal to not. I already have my local DNS pointing app.domain.com so this domain is resolved internally and resolved externally by a different server.

So how can apache2 tell if the connection comming in is from my own internal network? Is this possible. I have everything working now - the one url but everything is going over https.

Rgds
Chris

---

### Post by chrislynch8 on 2010-12-13
I have this soved for anyone Interested I used the Server_Addr parameter in my RewriteCond so when the external IP address is called via DNS it will redirect over https but when the Internal Server address is called https is not required

---

