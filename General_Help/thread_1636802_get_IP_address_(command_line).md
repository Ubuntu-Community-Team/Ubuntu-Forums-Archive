---
title: "get IP address (command line)"
date: 2010-12-03
forum: General Help
---

### Post by ddragas on 2010-12-03
Hi all

how can I get IP address (command line) of a remote machine that connects to my server on certain port and sends some packets/data

Any help is appreciated

kind regards

---

### Post by dcstar on 2010-12-04
> **ddragas said:**
> Hi all

how can I get IP address (command line) of a remote machine that connects to my server on certain port and sends some packets/data

Any help is appreciated

kind regards

```
netstat -a
```

---

### Post by ddragas on 2010-12-04
Hi

Thank you for reply.

This shows all IP addresses which have connected to my machine and vice versa.
I need only to get one which has just connected to my server and that is sending packets.

Is there this possibility with netstat?

---

