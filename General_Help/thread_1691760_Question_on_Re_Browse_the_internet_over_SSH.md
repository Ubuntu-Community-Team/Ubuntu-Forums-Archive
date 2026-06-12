---
title: "Question on Re: Browse the internet over SSH"
date: 2011-02-20
forum: General Help
---

### Post by renebs on 2011-02-20
Hi,

I have the following problem for which I would appreciate any help. The goal is to run Sage (sagemath.org) server without running a webserver. 

What I am doing right now is I log into a server via SSH ('ssh -D9999 server.ip'), and run sage in that server. However, I would like to be able to use Sage's web interface, normally just need to run 'sage -n' and open [http://localhost:8000](http://localhost:8000). But, no surprise, this address opens the local computer localhost, and not the server computer localhost, regardless of the fact that socks is configured to browse the internet via port 9999 (effectively I am browsing the internet using the server ip, I checked using whatismyip.com) 

Thanks for reading it,


UPDATE: well, I was able to solve my problem with further reading. What I needed was port-forwarding directly and not dynamic port forwarding, this link was helpful [http://www.linuxhorizon.ro/ssh-tunnel.html](http://www.linuxhorizon.ro/ssh-tunnel.html), basically solution is 

```
ssh -L 8888:localhost:8000 user@server
```
and open your browser to localhost:8888 no need to configure socks/proxy on your server.

---

