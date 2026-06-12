---
title: "hybrid ircd not connected?"
date: 2010-03-17
forum: General Help
---

### Post by mwjones on 2010-03-17
When attempting to use my ircd, I am receiving the following message in irrsi:

```
-!- Irssi: Looking up 127.0.0.1
-!- Irssi: Connecting to 127.0.0.1 [127.0.0.1] port 6667
-!- Irssi: Connection to 127.0.0.1 established
-!- Irssi: !hybrid7.debian.local *** Looking up your hostname...
-!- Irssi: !hybrid7.debian.local *** Checking Ident
-!- Irssi: !hybrid7.debian.local *** No Ident response
```

Looks good, connection shows up in netstat, etc.  But if I try to join a channel, I get:

```
-!- Irssi: Not connected to server
```

I've also tried connecting to the IP address on eth2, which is the only interface with an IP, and the same result occurs.

This has been attempted with the default install config, and a slightly modified config:

```
--- ircd.conf.orig
+++ ircd.conf

- hub = yes;
+ hub = no;

- host = "127.0.0.1"; # change this!
+ # host = "127.0.0.1"; # change this!

deny {
- ip = "10.0.1.0/24";
+ # ip = "10.0.1.0/24";
```

Behavior from hybrid ircd is the same regardless of which config is used.

The IP address is statically assigned from /etc/network/interfaces, as is the gateway.  This box is just on a hub with one other system.  There is one iptables rule present and it is in the PREROUTING chain of the NAT table, and it does not increase so I assume it is irrelevant, but here is the rule:

```
iptables -t nat -I PREROUTING -i eth2 -j REDIRECT
```

I'm really at a loss here on how to get the IRC daemon to work properly.  Any help would be greatly appreciated.  TIA!

---

### Post by mwjones on 2010-03-17
The iptables policies (-P) are all ACCEPT, and I also tried deleting the one rule in PREROUTING but still no luck.

---

### Post by mwjones on 2010-03-17
I have also been tailing the log, and no error messages appear.

---

