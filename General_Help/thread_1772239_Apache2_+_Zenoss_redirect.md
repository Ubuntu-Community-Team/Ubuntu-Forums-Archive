---
title: "Apache2 + Zenoss redirect"
date: 2011-05-31
forum: General Help
---

### Post by syafu on 2011-05-31
Hi all,

Sorry if my grammar is bad.

I configure apache2 to provide https to zenoss.
I redirect https traffic to port 8080 (zenoss default port).

Internal network --> https --> redirect --> 127.0.0.1:8080 (zenoss)

RewriteRule below run smoothly:
[https://10.1.31.193/](https://10.1.31.193/)  --> redirect --> 127.0.0.1:8080

```
RewriteRule ^/(.*) \ http://127.0.0.1:8080/VirtualHostBase/https/10.1.31.193:443/$1 \ [L,P]
```

But when I want to redirect /zenoss it fail:
[https://10.1.31.193/zenoss/](https://10.1.31.193/zenoss/) --> redirect --> 127.0.0.1:8080

```
RewriteRule ^/zenoss/(.*) \ http://127.0.0.1:8080/VirtualHostBase/https/10.1.31.193:443/zenoss/$1 \ [L,P]
```

Im not sure whether the regex is correct or not.

I want to put zenoss inside /zenoss because I want to run ganglia on the same machine.

With my limited knowledge on linux and already google, im not sure what is the problem and how to solve this.

Thanks in advance.

Rgds,
Syafu

---

### Post by syafu on 2011-06-20
I manage to find the solution. Replace zenoss to zport, it seem that zport is the document root for zenoss.

```
RewriteRule ^/zport(.*) \
http://%{SERVER_NAME}:8080/VirtualHostBase/\
https/%{SERVER_NAME}:443/VirtualHostRoot/zport/$1 [L,P]
```


Thanks.

---

