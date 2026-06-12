---
title: "How can I change the outgoing Telnet ports used?"
date: 2006-05-24
forum: General Help
---

### Post by CzarAlex on 2006-05-24
When I make outgoing telnet connections to other servers (in this case, MOOs, MUDs, MUSHs, and other text only RPG games), using linux, they seem to utilize ports 30000 through 60000. Here are a couple examples from `netstat`:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State   
tcp        0      0 192.168.1.30:49173      ata.be:1111             ESTABLISHED
tcp        0      0 192.168.1.30:36275      philote.endersgame:4500 ESTABLISHED
tcp        0      0 192.168.1.30:46983      adsl-68-121-149-23:9911 ESTABLISHED
```

When I connect to the same servers from Windows XP, the outgoing ports used range from 1000 through 5000.

Here's the thing. Due to my cruddy Linksys based router, If I do not port forward 1000 - 5000 to my Windows box and 30000 - 60000 to my Linux box, I cannot idle on these MOOs for more than 20 minutes without being disconnected. Forwarding the ports works just fine.

Id like to have a 2nd Linux box up and running that I'd like to connect with, but I can't forward 30000 - 60000 to two boxes. Can I change the outgoing ports that telnet, or the specific application (KMuddy) uses to connect to these services? Perhaps 10000-15000? Can this be done...and can I do it? :-k 

Thanks!

---

### Post by CzarAlex on 2006-05-24
Actually, I may have answered my own question, but let me know if this is what I'm looking for..

Right now, />/proc/sys/net/ipv4/ip_local_port_range has a value of 32768   61000

If I change that to 10000 15000 will that do what I need?

---

