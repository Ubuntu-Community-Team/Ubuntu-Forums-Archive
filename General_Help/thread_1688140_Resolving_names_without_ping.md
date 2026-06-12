---
title: "Resolving names without ping"
date: 2011-02-15
forum: General Help
---

### Post by jmvidalvia on 2011-02-15
Hi!
I need to check the output of a name resolution, but I configured the firewall of the destination to avoid answering to pings.
Is there any other way to get a name's IP without using ping? (I mean something like $resolv name.com)
Thanks!

---

### Post by Grenage on 2011-02-15
How about:

```
nslookup **hostname**
```

That uses your DNS server to lookup the host name.

---

### Post by jmvidalvia on 2011-02-15
Great!
Thanks.

jm

---

