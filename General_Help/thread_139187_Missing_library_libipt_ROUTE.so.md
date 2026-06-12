---
title: "Missing library libipt_ROUTE.so"
date: 2006-03-03
forum: General Help
---

### Post by steve.horsley on 2006-03-03
I am tinkering with iptables, and I get this error message
> root@Agatha:~# iptables -A FORWARD -t mangle -i eth0  -s 1.1.1.2 -j ROUTE
iptables v1.3.1: Couldn't load target `ROUTE':/lib/iptables/libipt_ROUTE.so: cannot open shared object file: No such file or directory

Can anyone please point me in the right direction for getting hold of this library file? 
Thanks.

---

### Post by Xian on 2006-03-03
That lib is in the Debian version of [iptables](http://packages.debian.org/testing/net/iptables) but not included in Ubuntu's build.
I have no explanation for this occurance.

---

### Post by steve.horsley on 2006-03-04
Thanks for the pointer. Unfortunately, they don't seem to hold a version 1.3.1 which seems to be what Ubuntu needs. I'll try to figure out another way round the problem.

---

