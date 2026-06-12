---
title: "setting up dyndns host to point to home web server"
date: 2009-11-24
forum: General Help
---

### Post by lauragarcia on 2009-11-24
Hi everyone,

I'm new to linux ubuntu and loving it, Anyhow i have three physical servers each running Apache2, PHP, I keep My MYSQL on a separate Server Behind a monowal firewall which is a cluster server.
Anyway way i created three Dyndns host names. example1.selfip.net, example2.selfip.net and example3.selfip.net now my problem is getting my host names to access the my servers basically if i type any of the host [http://example1.selfip.net](http://example1.selfip.net) to 3 I get the same server all there servers are on the same network sharing the single IP I have. 

I tried solving this problem with NAT but it only works if i type 

[http://example1.selfip.net](http://example1.selfip.net)  ----> takes me to default port 80 on server 1
[http://example2.selfip.net:81](http://example2.selfip.net:81)  ----> takes me to default port 80 on server 2
[http://example3.selfip.net:82](http://example3.selfip.net:82)  ----> takes me to default port 80 on server 3

What i want to do is use one Dyndns host name example.selfip.net work like so

[http://webserver1.example.selfip.net](http://webserver1.example.selfip.net) ----> take me to server1 on my local network
[http://webserver2.example.selfip.net](http://webserver2.example.selfip.net) ------> takes me to server 2 and so on.

basically i want to have sub domains. i have an internal DNS server and a cashing server each running on separate boxes. the question is how do i get my DNS server to answer the request for the given host name and return the FQDN e.g server1.example.selfip.net to point to Server 1,2 or 3.

Any ideas on this would be greatly appreciated, I've been banging my head on my keyboard too long on this problem and google isn't helping

Thanks Laura

---

### Post by dcstar on 2009-11-24
> **lauragarcia said:**
> Hi everyone,

I'm new to linux ubuntu and loving it, Anyhow i have three physical servers each running Apache2, PHP, I keep My MYSQL on a separate Server Behind a monowal firewall which is a cluster server.
Anyway way i created three Dyndns host names. example1.selfip.net, example2.selfip.net and example3.selfip.net now my problem is getting my host names to access the my servers basically if i type any of the host [http://example1.selfip.net](http://example1.selfip.net) to 3 I get the same server all there servers are on the same network **sharing the single IP I have**. 
........

Use Apache redirects to point the other sites to the other ports (81, 82, whatever):

[http://www.akadia.com/services/apache_redirect.html](http://www.akadia.com/services/apache_redirect.html)

---

### Post by Cheesemill on 2009-11-24
There was a very similar question asked yesterday, check out bodhi.zazen's excellent answer:

[http://ubuntuforums.org/showthread.php?t=1335677](http://ubuntuforums.org/showthread.php?t=1335677)

---

### Post by lauragarcia on 2009-11-25
Thanks for your speedy response I'll let you know how i fare out.

Laura

---

