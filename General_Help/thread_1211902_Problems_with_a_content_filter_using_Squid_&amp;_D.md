---
title: "Problems with a content filter using Squid &amp; Dansguardian"
date: 2009-07-13
forum: General Help
---

### Post by Jarr0d on 2009-07-13
Hello Guys,

I have built a handful of proxy servers before using the following guide. But since the release of Ubuntu 9.04, Dansguardian 2.9.9.7 and squid 2.7 stable this guide is giving me issues.

I have followed the guide and appended the steps to suit the config changes.

Previously, I have had the machines browse through the proxy using the port 3128.

This is a the guide I am using. It was written by myself about a year ago. [http://www.ganish.net/jar/guide.txt](http://www.ganish.net/jar/guide.txt)

After the build, the box starts working like normal. It is filtering like it should and seems to be working.
A tech than takes the machine to the clients, assigns a static IP through the GUI and all hell breaks loose.
I can no longer browse through 3128, the browser times out. 

If I use the GUI to change the IP back to dynamic it still doesn't kick over. So far I have found the only way to get it alive again, is to do a complete rebuild. As I have done once before.

So I have come to the conclusion that assigning the IP is where my system falls over.

If I look in /etc/network/interfaces I see:

```

auto lo
iface lo inet loopback

pre-up iptables-restore < /etc/iptables.rules

```

Wouldn't the assigning of the IP through the GUI show up in /etc/network/interfaces?

Anyway

My squid.conf has the following

```

acl localnet src 192.168.0.0/24 # RFC1918 possible internal network

acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 3128          # squid
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
acl our_networks src 192.168.0.0/24
http_access allow our_networks

http_access allow localnet
http_access allow localhost

```

I know that the network has been defined twice, this is one of the attempts I have made trying to revive it.

My iptables show that the Iptable rule is running ok

```

iptables -t nat -n -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3128 redir ports 8080

```

I am running the following

Ubuntu 9.04 

Package: dansguardianVersions:
2.9.9.7-2ubuntu1 

Package: squid
Versions:
2.7.STABLE3-4.1ubuntu1 



Can someone see something I have missed?

Or

What else do I need to put up for troubleshooting purposes?


Thanks

---

### Post by Jarr0d on 2009-07-13
Bump

---

