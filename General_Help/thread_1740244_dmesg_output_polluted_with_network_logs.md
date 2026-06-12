---
title: "dmesg output polluted with network logs"
date: 2011-04-26
forum: General Help
---

### Post by bobdobbs on 2011-04-26
Hi all.

Occaisonally I use 'dmesg' to see what's happening with my system. 

Lately I've noticed something that I've never seen before: the output from dmesg is polluted with logs of network packets.


At the moment, the output of 'dmesg' looks like this:

```

[312682.369635] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:25:b8:a2:00:14:7f:ff:5d:00:08:00 SRC=58.28.25.10 DST=192.168.1.71 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=43581 WINDOW=0 RES=0x00 RST URGP=0 
[312683.393141] [UFW BLOCK] IN=eth0 OUT= MAC=00:1e:8c:25:b8:a2:00:14:7f:ff:5d:00:08:00 SRC=58.28.25.10 DST=192.168.1.71 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=43582 WINDOW=0 RES=0x00 RST URGP=0 
```

... and so on.

How can I make dmesg useful to me again?

---

### Post by graysky on 2011-08-10
You can't... but you can remove these lines as they are printed with sed for example.

```
$ dmesg | sed '/UFW/d'p
```

If it really bugs you, bind the above to an alias for dmesg in your ~/.bashrc and you're good.

---

