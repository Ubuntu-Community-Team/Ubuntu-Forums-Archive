---
title: "Update 12.04 behind proxy server??"
date: 2012-05-12
forum: General Help
---

### Post by improud2b on 2012-05-12
hello..friends..

i have been using ubuntu 10.04 for about 1 year..

i am very much used to with 10.04..now i m planing to go for 12.04..so i just tried it with USB..

but i have little doubt that new 12.04 doesn't contain synaptic package manager..right?

actually i must have to have synaptic package manager in order to update my Ubuntu..

actually i m behind the proxy ,i am on LAN connection in University ...

they are not allowing Ubuntu software center to connect to Ubuntu servers..
they are blocking access...

i am not able to install app or update behind proxy sever..

in 10.04 i figured out that if we just put proxy setting in synaptic package manager then update will working fine..


since 12.04 doesn't have synaptic package manager..i an not able to get update and install software from Ubuntu software center...


so please help me guys...

---

### Post by Prescilla on 2012-05-12
Go to System Settings > Network > Network Proxy > Manual
and setup the proxy and the port

OR you can edit /etc/apt/apt.conf and add this
```
Acquire::http::proxy "http://host:port/";
Acquire::https::proxy "https://host:port/";
Acquire::ftp::proxy "ftp://host:port/";
Acquire::socks::proxy "socks://host:port/";

```

Edit:
see the attached image

---

### Post by improud2b on 2012-05-12
thanks,...i will try this and let you know..thanks..

in 10.04 ..i am able to getting update but i m not able to download from ubuntu software centre..

but my proxy also require Username and Password..

will this work?

thanks again..

---

### Post by Prescilla on 2012-05-12
This is the format if you use username and password:

```
Acquire::http::proxy "http://User:Password@host:port/";

Acquire::ftp::proxy "ftp://User:Password@host:port/";

Acquire::https::proxy "https://User:Password@host:port/";
```

---

