---
title: "Authoxy like linux app?"
date: 2010-07-24
forum: General Help
---

### Post by bacardiandwatermelon on 2010-07-24
Hey guys, is there a app similar to authoxy on os x that will forward all local traffic add proxy authentication and push it to your proxy server? I'm trying to find a better solution than manually changing proxy settings on certain apps that don't seam to follow the network proxy settings.. Cheers

---

### Post by bacardiandwatermelon on 2010-07-25
Bump

---

### Post by bahubindu on 2010-07-25
System>Preferences>Network Proxy.. enter the proxy info and click on details...

---

### Post by HermanAB on 2010-07-25
iptables --redirect

and socat

---

### Post by bacardiandwatermelon on 2010-11-16
Just thought i'd add this incase this pops up in the future. I used an app called cntlm. Basically I configured it to listen 8080 and forward it onto my proxy with authentication. Was really handy for few apps I had that wouldn't let you add your username/password etc.

---

### Post by rajun198 on 2011-08-28
> **HermanAB said:**
> iptables --redirect

and socat
Actually i am new user to ubuntu.I am working under a squid LDAP authentication based proxy.
When i use flash player related sites the flashplayer dont use authentication from system setting hence these applications dont work.so i want aauthoxy like s/w .

Can you help me please an d let me know how to use "socat" or any other s/w that can do my job.

THANKS IN ADVANCE:)

---

