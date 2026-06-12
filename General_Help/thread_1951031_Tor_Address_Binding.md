---
title: "Tor Address Binding"
date: 2012-04-01
forum: General Help
---

### Post by Kodeine on 2012-04-01
Salutations!

So I've installed Tor and the Vidalia frontend. I've forwarded a custom port on my router and changed the IP and port in the advanced settings section under 'Use TCP connection (controlport)'. But it gives me this log.

```
Apr 02 01:03:36.998 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 02 01:03:36.998 [Notice] Initialized libevent version 2.0.12-stable using method epoll. Good.
Apr 02 01:03:36.998 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 02 01:03:36.998 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 02 01:03:36.998 [Notice] Opening Control listener on 127.0.0.1:4004
Apr 02 01:03:36.998 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:4004
Apr 02 01:03:36.998 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 02 01:03:36.998 [Error] Reading config failed--see warnings above.
```
Here's a picture of my settings. I put the custom port I forwarded and the 'server IP address' as it's called, from my router's forwarding configuration page.
[http://www.fayp.com/vi-zPffN6.png](http://www.fayp.com/vi-zPffN6.png)

---

