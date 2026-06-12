---
title: "Can't access internet on my ubuntu server setup"
date: 2011-07-08
forum: General Help
---

### Post by void0 on 2011-07-08
Hello,

First off - I'm running 11.04 as a VPS on an OpenVZ.

I've set up a very basic environment of LAMP + mail server. Installing apache, php, mysql and proftpd all went fine, but whenever I install iRedMail (which is postfix + dovecot + clamav and few more packages) I lose the internet connection.

Although the server is easily reachable by ssh and http, I can't connect anywhere from the server. At first I thought it only had issues with resolving domain names, but now I see it doesn't even ping IPs as well.

```

# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6762 (6.7 KB)  TX bytes:6762 (6.7 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:1243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1226 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:249817 (249.8 KB)  TX bytes:173078 (173.0 KB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:79.98.xxx.xxx P-t-P:79.98.xxx.xxx Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

# cat /etc/hosts
127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
79.98.xxx.xxx server.xxxxxx.com server

# cat /etc/hostname
server


```Any ideas where do I begin looking for problems??

Thanks a lot!

---

### Post by void0 on 2011-07-08
bump? :(

---

