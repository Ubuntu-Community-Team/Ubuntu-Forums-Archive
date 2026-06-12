---
title: "can't follow syslog - fills up with &quot;nullmailer failures&quot;"
date: 2010-12-31
forum: General Help
---

### Post by jimmy the saint on 2010-12-31
Hey,

I am trying to troubleshoot an openvpn connection, but the syslog is useless because it fills up with thousands of lines like this.

```

Dec 31 12:57:05 ubu-timeline nullmailer[16094]: smtp: Failed: Connect failed
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Sending failed:  Host not found
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Starting delivery: protocol: smtp host: mail. file: 1276772401.3232
Dec 31 12:57:05 ubu-timeline nullmailer[16095]: smtp: Failed: Connect failed
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Sending failed:  Host not found
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Starting delivery: protocol: smtp host: mail. file: 1291348801.8650
Dec 31 12:57:05 ubu-timeline nullmailer[16096]: smtp: Failed: Connect failed
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Sending failed:  Host not found
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Starting delivery: protocol: smtp host: mail. file: 1292997601.21684
Dec 31 12:57:05 ubu-timeline nullmailer[16097]: smtp: Failed: Connect failed
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Sending failed:  Host not found
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Starting delivery: protocol: smtp host: mail. file: 1288476001.29098
Dec 31 12:57:05 ubu-timeline nullmailer[16098]: smtp: Failed: Connect failed
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Sending failed:  Host not found
Dec 31 12:57:05 ubu-timeline nullmailer[1896]: Delivery complete, 1300 message(s) remain.

```

wtf is going on here?  I don't run a mail server or anything like that from my laptop.  They just keep on coming.

Thanks

---

### Post by wojox on 2010-12-31
What if you open a terminal and remove it:

```
sudo apt-get purge nullmailer
```

---

