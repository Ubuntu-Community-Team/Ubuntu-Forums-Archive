---
title: "How can I find what inbound ports are blocked"
date: 2012-09-03
forum: General Help
---

### Post by SeaHawk22 on 2012-09-03
How can I find what inbound ports are blocked

---

### Post by Habitual on 2012-09-03
[http://www.t1shopper.com/tools/port-scan/](http://www.t1shopper.com/tools/port-scan/)
or
```
for i in `seq 1024` ; do (echo >/dev/tcp/localhost/$i) &>/dev/null && echo "TCP port $i open"; done
```TCP port 22 open
TCP port 37 open
TCP port 113 open
TCP port 631 open

the rest are closed.

---

### Post by SeaHawk22 on 2012-09-03
Interesting, the website stated that
(netbios-ssn).
(microsoft-ds).

were closed, but the terminal command said they were open.

---

### Post by dcstar on 2012-09-04
> **SeaHawk22 said:**
> Interesting, the website stated that
(netbios-ssn).
(microsoft-ds).

were closed, but the terminal command said they were open.

One is testing what is running on your system and the other is testing what is visible from the Internet.

Massive difference.

---

