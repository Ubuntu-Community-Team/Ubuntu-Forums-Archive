---
title: "Configuring Tor in Ubuntu 11.10"
date: 2011-11-14
forum: General Help
---

### Post by rikugo1 on 2011-11-14
I have installed everything, but seem to be having a permissions issue. Here's the error I'm getting:

```
Nov 14 17:30:17.771 [Notice] Tor v0.2.2.34 (git-c55c166e73d500af). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Nov 14 17:30:17.771 [Notice] Initialized libevent version 1.4.14b-stable using method epoll. Good.
Nov 14 17:30:17.771 [Notice] Opening Socks listener on 127.0.0.1:9050
Nov 14 17:30:17.771 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Nov 14 17:30:17.771 [Notice] Opening Control listener on 127.0.0.1:9051
Nov 14 17:30:17.771 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Nov 14 17:30:17.772 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Nov 14 17:30:17.772 [Error] Reading config failed--see warnings above.
```

---

### Post by theophiles on 2011-12-01
I found help here:
[http://ubuntuforums.org/showpost.php?p=9226418&postcount=3](http://ubuntuforums.org/showpost.php?p=9226418&postcount=3)

---

