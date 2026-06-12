---
title: "Ping (out) Through Firewall"
date: 2012-02-01
forum: General Help
---

### Post by jim_deadlock on 2012-02-01
My /etc/ufw/before.rules is default and has never been edited since system install but UFW is still blocking my pings (out). Any suggestions?

/etc/ufw/before.rules
```
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```

/var/log/syslog
```
Feb  1 18:02:01 nova kernel: [21492.094530] [UFW BLOCK] IN= OUT=eth0 SRC=xx.xx.xx.xx DST=72.30.2.43 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=9508 SEQ=1 
Feb  1 18:02:02 nova kernel: [21493.102241] [UFW BLOCK] IN= OUT=eth0 SRC=xx.xx.xx.xx DST=72.30.2.43 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=9508 SEQ=2 
Feb  1 18:02:03 nova kernel: [21494.109026] [UFW BLOCK] IN= OUT=eth0 SRC=xx.xx.xx.xx DST=72.30.2.43 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=9508 SEQ=3 

```

---

### Post by Dangertux on 2012-02-01
Try adding the following rule

```

-A ufw-before-output -p icmp --icmp-type echo-request -j ACCEPT

```

Hope this helps.

---

### Post by jim_deadlock on 2012-02-01
Thanks, it's obvious when you know how :D

---

