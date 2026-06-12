---
title: "Huludesktop and socks server"
date: 2011-02-10
forum: General Help
---

### Post by rlongfield on 2011-02-10
I am trying to get Huludesktop up and running through my socks server.
I have tried socksifying the program but it doesn't go through my socks server. 

I've tried the following:

export SOCKS_SERVER=10.8.0.1
socksify application

I have also tried with this socks.conf file:

route {
    from 0.0.0.0/0 to 0.0.0.0/0 via 10.8.0.1 port = 1080
    proxyprotocol: socks_v5
    proxyprotocol: socks_v4


What happens is I get a huludesktop window that opens, but it remains white and then it crashes with a GTK error. When I run huludesktop without socksifying it, it opens up just fine.

Is this because I'm not listening on the right port in the socks server?

thanks

---

