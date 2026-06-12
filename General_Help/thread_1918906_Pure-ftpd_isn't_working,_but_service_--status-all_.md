---
title: "Pure-ftpd isn't working, but service --status-all shows it's running?"
date: 2012-02-01
forum: General Help
---

### Post by ingramproductions on 2012-02-01
Pure-ftpd stopped working for me. when I run *service --status-all*, I see *[ - ]  pure-ftpd*, and when I run nmap localhost, port 21 isn't listed.
Is there anything else I can do to find out why it's not working?

I'm using 10.04 server edition 64 bit

---

### Post by ingramproductions on 2012-02-03
Think I found out what was causing it. Every time I try to restart pure-ftpd, I get this in /var/log/syslog:
```
pure-ftpd: (?@?) [ERROR] Sorry, but that file doesn't exist: [/etc/ssl/private/pure-ftpd.pem]
```

---

