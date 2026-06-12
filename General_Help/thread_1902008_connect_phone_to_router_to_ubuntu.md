---
title: "connect phone to router to ubuntu?"
date: 2011-12-29
forum: General Help
---

### Post by loolooyyyy on 2011-12-29
hi, it's a bit complicated for me
i have an andriod phone, having a proxy application giving me the options:
Proxy settings:
  Host:
  Port:
  Proxytype:HTTP/SOCKS4/SOCKS5
account information:
 User:
 Password:

there is a wireless modem/router android is connected to, and has obtained ip address: 192.168.1.5

the ubuntu-pc is connected to router has obtained ip address: 192.168.1.4
ubuntu is connected to SERVER-1 using ssh root@SERVER-1 -D 9999
which is creating a SOCKS proxy on 127.0.0.1 on port 9999

so now i need to connect andriod through router to ubuntu, and then tell it to use socks on ubuntu
and now, android browser uses SOCKS proxy of ubuntu

what should i do in proxy application of andriod AND on ubuntu?

i should say "I HAVE TO USE THIS CONFIGURATION!!!"
it will be not be possible to use a socks proxy directly, for some reasons....
can you help?

---

