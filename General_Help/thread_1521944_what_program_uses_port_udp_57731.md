---
title: "what program uses port: udp 57731"
date: 2010-07-01
forum: General Help
---

### Post by markp1989 on 2010-07-01
friends ubuntu laptop is at my house, and im seing alot of out bound trafic on that port udp 57731 (average about 20kbs) i closed all programs running the internet and the data is still being sent.

any known programs that use udp port 57731?

edit: i thnk deluge was using that port  earlier today, but i have exited deluge, and there is still data coming from it? 

edit: i have also tried changing deluge port to a different one, and even with no torrents running, im still seing data on my router, and iftop. 

thanks, mark

---

### Post by pricetech on 2010-07-01
According to IANA 49152 to 65535 are Dynamic / Private ports.  Nothing is assigned to use that port.  As such, it could be anything.

---

### Post by CharlesA on 2010-07-01
What does this return?

```
sudo netstat -lupn
```

---

