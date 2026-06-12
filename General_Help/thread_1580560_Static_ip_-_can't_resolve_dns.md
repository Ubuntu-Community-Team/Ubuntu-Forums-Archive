---
title: "Static ip - can't resolve dns"
date: 2010-09-23
forum: General Help
---

### Post by ALnot on 2010-09-23
New guy.

I am trying to set a static ip in Ubuntu 10.04 so I can use NX client on my Vista box.

auto eth1
iface eth1 inet static 
          address 192.168.0.100         
  netmask 255.255.255.0         
  network 192.168.0.0         
  broadcast 192.168.0.255 
          gateway 192.168.0.1 

That seems right to me.
However, when I try to use the Internet I can't get out. That seems like
a dns issue to me, when I ping google from a terminal I get: 
unknown host [www.google.com]("http://www.google.com").

If some one can point me in the right direction I know I can fix this.

Thanks -

ALnot.

---

### Post by ALnot on 2010-09-23
SOLVED 

It was resolve.conf needed to add nameserver to list

thanks for all the help!

---

