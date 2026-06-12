---
title: "DNS &amp; Bind Help"
date: 2011-02-23
forum: General Help
---

### Post by diamondf on 2011-02-23
Hey everyone,

I'm in need of some serious help. I've been bashing my head against a wall all day, trying to go to several different people and help groups. It started with thinking it was nginx that I was having a problem with, to DNS registration name servers, and now it seems that bind is the problem. Here's what's going on.

I have a new server with ubuntu 10.04, and nginx / php-fpm installed. I configured nginx so that I can view it with [http://the.ip.it.has/](http://the.ip.it.has/)

However, when I point the DNS I own toward it ([http://mysite.com](http://mysite.com)), the server just says "Server not found" - the name server has propogated, and it's been over 2 days. I started messing around with bind, but when I make changes that seem right to me, bind doesn't start. I'm not all that great with server administration, but I really need this system to be working for me.

Can somebody PLEASE help me with this... I will gladly sit here and walk you through step by step what I need, or I will gladly pay somebody to jump into my server and set up the bind/whatever dns thing this is for me. I just can't have this server down for as long as it takes me to teach myself everything necessary for this.

My bind file (the named.conf.local) currently has no zone in it (as I said, when I try to set this up, bind won't start for me). I've read through tutorials that just say "Oh, set it to this" with no luck. Please help :confused:

---

