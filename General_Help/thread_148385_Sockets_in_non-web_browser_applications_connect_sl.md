---
title: "Sockets in non-web browser applications connect slowly"
date: 2006-03-22
forum: General Help
---

### Post by wkh on 2006-03-22
Hi,

When I first installed Ubuntu I had to disable IPv6 in order to get reasonable response times in Epiphany/Firefox. So I've seen the stuff about doing that to increase web browsing speed. That's fine, that isn't the problem.

The problem is that other applications (e.g. Python code that downloads stuff over HTTP) connect very slowly the way my web browser did before I disabled IPv6. Does anyone know a way to deal with this?

---

### Post by joshuapurcell on 2006-03-22
This is a weird problem. I heard that some people noticed faster response times when disabling IPv6, but I never noticed a difference with this. Do you use a router? If so, have you eliminated that as being the point of slowdown to making the connection? I'm thinking on the lines of DNS more than anything... if you are using IP addresses then this probably wouldn't apply. Sometimes routers that are handing out their own IP address as a DNS server to clients slow the process of name resolution down considerably.

---

