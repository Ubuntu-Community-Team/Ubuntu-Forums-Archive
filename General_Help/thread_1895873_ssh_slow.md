---
title: "ssh slow?"
date: 2011-12-15
forum: General Help
---

### Post by loolooyyyy on 2011-12-15
using ubuntu 11.10
i use ssh to create a socks proxy on port xxxx  by this command:
$ ssh [email]user@yyy.yyy.yyy.yyy[/email] -D xxxx
and set firefox socks proxy to localhost on port xxxx

i dont touch anything for 2minutes, i open a page, speed is ok, it's good actually
after a few minutes of browsing it becomes totally useless because of low speed
again, i dont touch anything for 2 minutes, speed is good again for first 2 or 3 pages, then again..... and so on

ipv6 is globally disabled using 
user@pc:$ sudo -i
root@pc:$ echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6


also disabled in firefox

and also, asuming sshServer in germany, serverA in germany also,my PC in my country, i have:
sshServer ping to serverA:about 15ms , through ssh shell
PC ping to serverA: 300ms , through ubuntu's shell
inside firefox using socks it's 800ms!!!
it's so painful
any suggestions?

---

