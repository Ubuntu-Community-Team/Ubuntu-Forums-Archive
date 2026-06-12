---
title: "DNS Problem"
date: 2009-06-29
forum: General Help
---

### Post by Dan1317 on 2009-06-29
Hello, I am having a problem with my DNS server.  I have been learning about DNS and wanted to set one up for myself.  (The book I am reading is excellent)  Sadly, I cannot figure out my errors.  I have tried many times to understand and research but have come up with nothing.  I would be very grateful if someone could help me or point me in the right direction.

Every setting in /etc/bind looks right to me, but in /var/log/syslog this is shown when bind starts up:

```
Jun 29 00:24:34 ns1 named[4848]: starting BIND 9.4.2-P2 -u bind
Jun 29 00:24:34 ns1 named[4848]: found 1 CPU, using 1 worker thread
Jun 29 00:24:34 ns1 named[4848]: loading configuration from '/etc/bind/named.conf'
Jun 29 00:24:34 ns1 named[4848]: listening on IPv6 interfaces, port 53
Jun 29 00:24:34 ns1 named[4848]: listening on IPv4 interface lo, 127.0.0.1#53
Jun 29 00:24:34 ns1 named[4848]: listening on IPv4 interface eth0, 192.168.0.101#53
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: D.F.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 8.E.F.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: 9.E.F.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: A.E.F.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: automatic empty zone: B.E.F.IP6.ARPA
Jun 29 00:24:34 ns1 named[4848]: command channel listening on 127.0.0.1#953
Jun 29 00:24:34 ns1 named[4848]: command channel listening on ::1#953
Jun 29 00:24:34 ns1 named[4848]: zone 0.in-addr.arpa/IN: loaded serial 1
Jun 29 00:24:34 ns1 named[4848]: zone 127.in-addr.arpa/IN: loaded serial 1
Jun 29 00:24:34 ns1 named[4848]: zone 0.168.192.in-addr.arpa/IN: loaded serial 2009062801
Jun 29 00:24:34 ns1 named[4848]: zone 255.in-addr.arpa/IN: loaded serial 1
Jun 29 00:24:34 ns1 named[4848]: dns_rdata_fromtext: /etc/bind/zones/example.com.db:16: near 'mail.example.com.': not a valid number
Jun 29 00:24:34 ns1 named[4848]: zone example.com/IN: loading from master file /etc/bind/zones/example.com.db failed: not a valid number
Jun 29 00:24:34 ns1 named[4848]: zone localhost/IN: loaded serial 2
Jun 29 00:24:34 ns1 named[4848]: running

```

"Jun 29 00:24:34 ns1 named[4848]: zone example.com/IN: loading from master file /etc/bind/zones/example.com.db failed: not a valid number"   I don't understand this


I have attached my zone file and named.conf.local

Again, any help would be extremely appreciated




Edit: I fixed the issue, sorry for the bother.  Could a mod delete this please?

---

