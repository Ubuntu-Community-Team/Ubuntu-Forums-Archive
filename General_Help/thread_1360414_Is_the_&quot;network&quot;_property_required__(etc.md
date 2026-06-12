---
title: "Is the &quot;network&quot; property required?  (/etc/network/interfaces)"
date: 2009-12-20
forum: General Help
---

### Post by Skidbladniir on 2009-12-20
Could I use this:
```

address 70.114.165.30
gateway 70.114.160.1
netmask 225.225.225.0

```?

I heard some properties weren't required (like broadcast), and was wondering if network was one of them.

---

### Post by snova on 2009-12-20
> **Skidbladniir said:**
> Could I use this:
```

address 70.114.165.30
gateway 70.114.160.1
netmask 225.225.225.0

```?

I heard some properties weren't required (like broadcast), and was wondering if network was one of them.

I don't know about the validity of the file itself, but the network property doesn't seem to be necessary.

From the interfaces manpage:

```

              network network_address
                     Network address (dotted quad) required for 2.0.x kernels

```

Also, I use this file, and don't have one.

---

