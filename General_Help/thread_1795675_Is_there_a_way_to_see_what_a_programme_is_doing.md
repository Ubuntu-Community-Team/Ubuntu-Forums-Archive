---
title: "Is there a way to see what a programme is doing?"
date: 2011-07-03
forum: General Help
---

### Post by bowlofducks on 2011-07-03
As in, what files it's accessing on my PC, what web addresses it's talking to. Things like that.

---

### Post by HermanAB on 2011-07-03
tcpdump, gdb

---

### Post by Bachstelze on 2011-07-03
To list the opened file descriptors of a process:

```
ls -l /proc/PID/fd
```

With PID being the PID of the process, of course. To know the IP addresses it's connected to, you can use Wireshark.

---

