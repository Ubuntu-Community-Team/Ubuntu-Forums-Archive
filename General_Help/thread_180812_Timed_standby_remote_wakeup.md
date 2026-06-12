---
title: "Timed standby remote wakeup"
date: 2006-05-23
forum: General Help
---

### Post by gary79 on 2006-05-23
Hi,

Currently I am using 5.10 for a file server.

It is a bit of a power hungry beast - AMD 1700+. I would like to have the system suspend to ram after 20mins if not in use but would also need it to recover from standby when receiving a request for files via my LAN.

I've looked around this forum and goggled, but most of the information is about manual suspend/recovery.

Is this possible?

---

### Post by bluenova on 2006-05-23
Never tried it but maybe:
sudo apt-get install wakeonlan

---

