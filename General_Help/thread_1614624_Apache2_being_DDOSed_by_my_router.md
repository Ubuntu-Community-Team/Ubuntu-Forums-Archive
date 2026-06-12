---
title: "Apache2 being DDOSed by my router?"
date: 2010-11-05
forum: General Help
---

### Post by mrdek11 on 2010-11-05
Hi all, I'm running a LAMP server on 10.10 server.  I recently noticed that my router said it had 4,000 open connections, and saw they were all going to my server.  When I look at /var/log/access.log, I see hundreds of thousands of lines like this:

> 192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "Serf/0.3.1"
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /styles.css HTTP/1.1" 200 1197 "-" "Serf/0.3.1"


Somebody (who claims to be my router) is connecting to that page tens of times a second.  To see how it would respond, I tried throwing a 403 error to all people visiting that link, which seems to stop it for an hour or so, but now it seems to be getting these connections as well:

> 127.0.0.1 - - [05/Nov/2010:18:44:46 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [05/Nov/2010:18:44:47 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [05/Nov/2010:18:44:48 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [05/Nov/2010:18:44:49 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [05/Nov/2010:18:44:50 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"


As shown, those connections are coming in once per second.

Does anybody know what is going on here or how I can stop this?  My family's network is being constantly overloaded.

Thanks in advance,
Derek

[edit]In case it's relevant, my router is running DD-WRT v24-sp1 (07/27/08) std.

Looking at the connections in there, it said the source address was 192.168.0.108, my web server's address, and the remote address was my external IP address.  So my server is somehow getting in a loop and DDOSing itself?[/edit]

---

### Post by dcstar on 2010-11-05
> **mrdek11 said:**
> Hi all, I'm running a LAMP server on 10.10 server.  I recently noticed that my router said it had 4,000 open connections, and saw they were all going to my server.  When I look at /var/log/access.log, I see hundreds of thousands of lines like this:



Somebody (who claims to be my router) is connecting to that page tens of times a second.  To see how it would respond,
............
Looking at the connections in there, it said the source address was 192.168.0.108, my web server's address, and the remote address was my external IP address.  So my server is somehow getting in a loop and DDOSing itself?[/edit]

[LIST=1]
[*]Do not "quote" data.
[*]If you are using NAT, **all** external connections will be coming from your router.
[*]If you don't want to expose your internal web site to external attacks, turn off the port forwarding in your router.
[/LIST]

---

### Post by mrdek11 on 2010-11-06
Thanks for your helpful response. I am not using NAT, and the server IS external facing, but this attack started yesterday.

---

### Post by dcstar on 2010-11-06
> **mrdek11 said:**
> Hi all, I'm running a LAMP server on 10.10 server.  I recently noticed that my router said it had 4,000 open connections, and saw they were all going to my server.  When I look at /var/log/access.log, I see hundreds of thousands of lines like this:

```
192.168.0.1 - - [05/Nov/2010:18:42:28 -0600] "GET /sandbox/newinframe.php?item=skewered%20cherry HTTP/1.1" 404 - "-" "**Serf**/0.3.1"
```



Then you may want to look at that package and see what it is doing, or simply unplug the router and see if the requests stop.

---

### Post by dcstar on 2010-11-06
> **mrdek11 said:**
> Thanks for your helpful response. I am not using NAT, and the server IS external facing, but this attack started yesterday.

How can you server be "external facing" if it has a 192.168 address?

---

### Post by lisati on 2010-11-06
I notice the original log entries refer to **Serf/0.3.1**
You might find the comments [here]("http://download.famouswhy.com/serf/") interesting:
> Serf is a web server to prototype rich client-side web apps. It's a development tool to be used during the development of rich internet applications: **it's not intended for deployment**.

---

### Post by mrdek11 on 2010-11-09
> **dcstar said:**
> How can you server be "external facing" if it has a 192.168 address?

These connections are coming from my router to my server's internal ip address.


Edit: Found the source of the problem.  Google's new Apache2 module mod_pagespeed was causing it, no clue why, though.

---

### Post by hypest on 2010-11-19
Same behavior here... I thought I was attacked until I noticed that the "malicious" IP was my own external IP!

I've also installed mod_pagespeed a few days ago and moments ago suspected that maybe the mod was the root of the problem...

I'm disabling it now and see if the attack comes back...

---

### Post by mrdek11 on 2010-11-19
> **hypest said:**
> Same behavior here... I thought I was attacked until I noticed that the "malicious" IP was my own external IP!

I've also installed mod_pagespeed a few days ago and moments ago suspected that maybe the mod was the root of the problem...

I'm disabling it now and see if the attack comes back...

I haven't had any troubles since disabling the mod.  No clue what was going on!

---

### Post by hypest on 2010-11-19
it seems that is a known bug and still unresolved...

[http://code.google.com/p/modpagespeed/issues/detail?id=85](http://code.google.com/p/modpagespeed/issues/detail?id=85)

---

### Post by WorMzy on 2010-11-19
Regarding the "internal dummy connection" connections, those are normal. If I remember correctly, it's just the apache process managing it's threads. You can stop it logging those "connections" if you want, but I can't remember how. A google search may help in that regard.

EDIT: [http://wiki.apache.org/httpd/InternalDummyConnection](http://wiki.apache.org/httpd/InternalDummyConnection)

---

### Post by hypest on 2010-11-19
"internal dummy connection"s are normal indeed... but it's not that case here. The user agent string in the problematic connections is "Serf/0.3.1" and it's a bug alright.

---

### Post by WorMzy on 2010-11-19
I know, I'm just addressing the other half of the O/P.

---

### Post by hypest on 2010-11-19
> **WorMzy said:**
> I know, I'm just addressing the other half of the O/P.

oops, my bad :oops:

---

