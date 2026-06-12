---
title: "Complete system crash - probably due to vpnclient"
date: 2011-12-29
forum: General Help
---

### Post by TheSqueak on 2011-12-29
I've run into a major annoyance recently, in that my laptop will occasionally completely lock up, requiring a hard reboot to fix (even ssh sessions from other machines are frozen)

I *think* i've traced the issue to Cisco's vpnclient, and I was hoping that somebody else has seen this issue recently

I think it's the vpnclient because:

a) It only seems to happen at work when i've got it running
b) My syslog is **full** of

```
jme 0000:03:00.0: eth0: UDP Checksum error
```

entries, and I can see them filling it up whenever I pass any network traffic over the vpn.




For what it's worth, turning rx and tx checksumming offloading off stops the errors from filling up my logs, we'll see if it helps with any crashing

---

