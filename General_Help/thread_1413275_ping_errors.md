---
title: "ping errors"
date: 2010-02-22
forum: General Help
---

### Post by cucuru on 2010-02-22
hello, I',m executing ping, but it didn't work, in order to find the mistake in my network I would like to know how to see the errors:

```

18 packets transmitted, 0 received, +12 errors, 100% packet loss, time 17038ms
, pipe 4


```

I want to see this +12 errors. Could I do that?

Thanks! Regards!

---

### Post by wirelessmonkey on 2010-02-22
The output from above th line you posted contains the 'errors' example:


```

From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable
From 192.168.1.2 icmp_seq=5 Destination Host Unreachable
From 192.168.1.2 icmp_seq=6 Destination Host Unreachable
--- 192.168.1.2 ping statistics ---

9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8047ms
, pipe 3

```

Each of the "From" lines is one of the "+6" errors.

---

### Post by doas777 on 2010-02-22
you didn't run the ping with '-q' did you? if you did, then the errors are suppressed. just remove it and ping again.

---

