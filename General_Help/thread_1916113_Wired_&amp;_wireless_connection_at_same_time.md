---
title: "Wired &amp; wireless connection at same time"
date: 2012-01-27
forum: General Help
---

### Post by YigalB on 2012-01-27
My Ubuntu laptop has wired and wireless connections.
Each one have it own MAC address. 

What if both are enabled?
Will the laptop have 2 IPs? 
Which one will be used? 

Yigal

---

### Post by gsgleason on 2012-01-27
Both will have an IP address, yes, and it will use the interface dependent up on the kernel routing table.  I think network manager will prefer the wired.

While they're both connected, show the output of:
/sbin/route -n

---

