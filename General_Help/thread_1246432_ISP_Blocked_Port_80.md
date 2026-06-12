---
title: "ISP Blocked Port 80"
date: 2009-08-21
forum: General Help
---

### Post by cmoney12051 on 2009-08-21
so my isp blocked port 80. i am trying to figure out how to get port redirect working with no-ip. i went to no-ip and setup port redirect with port 8888 and changed my router port forwarding accordingly, and even setup ip masking in no-ip, but still cant get my site to show up, [http://cmoney12051.no-ip.biz/]("http://cmoney12051.no-ip.biz/"). i dont know what else to do. im using ubuntu server 8.10, linksys router, and its on a dynamic ip, but i use no-ip's auto update tool so its ok. please help.

---

### Post by harlan@bloomenterprises.o on 2009-08-21
> **cmoney12051 said:**
> so my isp blocked port 80. i am trying to figure out how to get port redirect working with no-ip. i went to no-ip and setup port redirect with port 8888 and changed my router port forwarding accordingly, and even setup ip masking in no-ip, but still cant get my site to show up, [http://cmoney12051.no-ip.biz/]("http://cmoney12051.no-ip.biz/"). i dont know what else to do. im using ubuntu server 8.10, linksys router, and its on a dynamic ip, but i use no-ip's auto update tool so its ok. please help.

Are you able to access your HTTP server locally from a different computer?  If so, then your ISP could be looking at the type of traffic you are trying to receive then blocking that traffic type (i.e. in-bound packets that contain HTTP data).

I'm unable to run an HTTP server that is accessible from the world because my ISP does this.  I can, however, run low-volume mail and VPN servers on non-standard ports.  MY ISP blocks all in-bound HTTP traffic, but the usual out-bound HTTP traffic.

---

### Post by cmoney12051 on 2009-08-21
yea i can access the pages locally, but thats it, i honestly dont know what there blocking, yesterday my site worked fine, now today i cant access it, not even if i type my internet ip in the address bar. someone told me they where probobly just blocking my port 80 but im not totally sure, i just know it worked yesterday and not today :(

---

### Post by credobyte on 2009-08-21
One of the easiest solutions is to use .htaccess file ( in most cases, it should work ).

```
Redirect 301 / [http://domain.com:8080/]("http://yourserver.com:8000/")
```

---

