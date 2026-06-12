---
title: "BIND Forwarders - Local First?"
date: 2010-04-09
forum: General Help
---

### Post by rockinthesixstring on 2010-04-09
I've just setup a Secondary Bind Server to serve requests when my primary goes offline.  I'm wondering that since the secondary server "should" only kick in if the primary is off line, is it worth it to put the primary servers IP as the first Forwarder?  Or do DNS lookups sometimes go directly to the Secondary server, in which case I want it to look in the local cache before checking outside the network.

```
forward first;
  forwarders {
    192.168.0.101;
    208.67.222.222;
    208.67.222.220;
    64.59.135.143;
    64.59.135.145;
  };
```

notice that the local 192.168.0.101 is the first in the list.

---

### Post by dcstar on 2010-04-10
> **rockinthesixstring said:**
> I've just setup a Secondary Bind Server to serve requests when my primary goes offline.  I'm wondering that since the secondary server "should" only kick in if the primary is off line, is it worth it to put the primary servers IP as the first Forwarder?  Or do DNS lookups sometimes go directly to the Secondary server, in which case I want it to look in the local cache before checking outside the network.

```
forward first;
  forwarders {
    192.168.0.101;
    208.67.222.222;
    208.67.222.220;
    64.59.135.143;
    64.59.135.145;
  };
```

notice that the local 192.168.0.101 is the first in the list.

If you want to wait for a timeout for a server that is obviously not going to respond, then add it to the list.

If the server does not even respond at all on Port 53 then the timeout may be short, if it just waits for a response that never comes on Port 53 then it will be longer.

---

