---
title: "Bittorrent - stuck on &quot;connecting to peers&quot;"
date: 2011-04-09
forum: General Help
---

### Post by kalebr on 2011-04-09
Hi folks,

Having trouble getting bt to work on my Ubuntu 10.10 server box.

I start it with 

```
btlaunchmanycurses downloads/ --minport 26900 --maxport 27100

```

But it just sits there reading "connecting to peers".  Doing some research, I've tried several things.

First of all, the ports appear to be opened on the firewall and forwarding to the correct ip.  Canyouseeme.org returns:
"Success: I can see your service on <ip hidden> on port (26900)"
Also, I'm sure it's a good tracker as it works correctly using uTorrent on my windows box.

netstat -plntu yields:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:30888           0.0.0.0:*               LISTEN      4765/tvmobilisvcd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      778/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      646/smbd
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      2712/perl
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      868/apache2
tcp        0      0 0.0.0.0:26900           0.0.0.0:*               LISTEN      6335/python
```

nmap localhost -p 26900

```
Starting Nmap 5.21 ( http://nmap.org ) at 2011-04-09 00:17 EDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000051s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
PORT      STATE SERVICE
26900/tcp open  unknown
```

iptables - L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

So, at this point, I have no idea what's wrong.  Any help would be greatly appreciated.

robbie

---

