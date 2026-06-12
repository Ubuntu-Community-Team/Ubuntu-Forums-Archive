---
title: "Firewall question"
date: 2010-01-23
forum: General Help
---

### Post by lemmy999 on 2010-01-23
My router has a firewall up and running as standard. I have installed Firestarter and can see a number of pings on the firewall 
> Time:Jan 23 08:49:47 Direction: Unknown In:eth1 Out: Port:51703 Source:99.52.178.128 Destination:192.168.1.91 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 23 09:04:02 Direction: Unknown In:eth1 Out: Port:64796 Source:78.164.193.219 Destination:192.168.1.91 Length:90 TOS:0x04 Protocol:UDP Service:Unknown
Time:Jan 23 09:04:58 Direction: Unknown In:eth1 Out: Port:64796 Source:121.31.60.36 Destination:192.168.1.91 Length:90 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan 23 09:05:45 Direction: Unknown In:eth1 Out: Port:51703 Source:99.52.178.128 Destination:192.168.1.91 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 23 09:11:16 Direction: Unknown In:eth1 Out: Port:51703 Source:222.131.82.73 Destination:192.168.1.91 Length:90 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan 23 09:12:24 Direction: Unknown In:eth1 Out: Port:51703 Source:99.52.178.128 Destination:192.168.1.91 Length:48 TOS:0x00 Protocol:TCP Service:Unknown

Does this mean that my hardware firewall is failing in its job?

---

### Post by d3v1150m471c on 2010-01-23
```

d3v11@d3v11m4ch1n3:~$ whois 192.168.1.91

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    http://www.arin.net/reference/rfc/rfc1918.txt
RegDate:    1994-03-15
Updated:    2007-11-27

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  abuse@iana.org

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  abuse@iana.org

```

...no

---

### Post by user1397 on 2010-01-23
i don't know about your router's firewall, but as far as ubuntu goes, it's ports are closed by default...so no one can see you unless you let them.

---

### Post by d3v1150m471c on 2010-01-23
> **ubuntuman001 said:**
> i don't know about your router's firewall, but as far as ubuntu goes, it's ports are closed by default...so no one can see you unless you let them.

Everyone and their brother can see him unless he has firestarter configured to silently drop incoming packets.

---

### Post by d3v1150m471c on 2010-01-23
Friendly advice - don't put your ip on public forums. Also, your firewall is working perfectly.

---

### Post by lemmy999 on 2010-01-23
192.168.1.91 is the IP of my desktop, not my external IP.

---

### Post by d3v1150m471c on 2010-01-23
Exactly, and your firewall is doing what it should. I know these things.

---

### Post by Ordes on 2010-01-23
... internal IP  doesnt really matter, as it says nothing about the destination.And by a guess, 2/3 either start with 192.168.2.100 or 192.168.1.1.100. The external IP is the important one.., but as most of us wont have a static IP, it will also keep on changing ....

---

