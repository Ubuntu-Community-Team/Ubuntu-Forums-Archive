---
title: "ssh_exchange_identification: Connection closed by remote host"
date: 2011-04-25
forum: General Help
---

### Post by markp1989 on 2011-04-25
have been able so ssh in to my pc everyday for the last year, today I tried to ssh in to it and I got this error?

```

mark@markslaptop:~$ ssh mark@torrentslave
ssh_exchange_identification: Connection closed by remote host

```

considering nothing has been changed by me , what could cause it to stop me getting in?

---

### Post by SexySara on 2011-04-25
What's in the logs on the server? It should give a reason.
Check /etc/hosts.allow and /etc/hosts.deny.

---

### Post by markp1989 on 2011-04-27
for some reason the machine had became unresponsive, I rebooted it and haven't had any problems since.

---

