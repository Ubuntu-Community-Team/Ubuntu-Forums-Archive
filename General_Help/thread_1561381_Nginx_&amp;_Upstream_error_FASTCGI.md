---
title: "Nginx &amp; Upstream error FASTCGI"
date: 2010-08-26
forum: General Help
---

### Post by Gordonisnz on 2010-08-26
Nginx error log

> 
[error] 3947#0: *1 connect() failed (111: Connection refused) while connecting to upstream, client: 127.0.0.1, server: SERVERNAME, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "SERVERNAME"


(I've replaced server name)

basically, I have set up NGINX - Which does work (no php). But when I try & load fastcgi, I get the above errors in my nginx log, & '502 Bad gateway' on my browser.

QUESTION :-

It seems to be trying fastcgi, on port 9000.

:- How do I find out the ACTUAL port number fastcgi is using ?

:- How do I tell nginx to use the (correct) port, to activate fastcgi.

---

