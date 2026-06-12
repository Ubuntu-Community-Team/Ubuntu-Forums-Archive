---
title: "Vidalia issues"
date: 2012-04-21
forum: General Help
---

### Post by joelstitch on 2012-04-21
I have Vidalia and Tor installed on my computer. Tor works just fine, it loads on the background on startup but when I open Vidalia I get this errors:

```
Apr 21 17:49:16.298 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 21 17:49:16.298 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 21 17:49:16.299 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 21 17:49:16.299 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 21 17:49:16.299 [Warning] /var/run/tor is not owned by this user (stitch, 1000) but by debian-tor (115). Perhaps you are running Tor as the wrong user?
Apr 21 17:49:16.299 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Apr 21 17:49:16.299 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 21 17:49:16.299 [Error] Reading config failed--see warnings above.
```

I like using Vidalia because it makes it easy to renew the Tor IP. Please help. Thank you.

---

### Post by joelstitch on 2012-04-21
I went to **Settings > Advanced > Tor Control **and checked **Use TCP Connection (ControlPort) **with the address **127.0.0.1:9051 **and now is working fine so far.

---

### Post by fester225 on 2012-06-07
> **joelstitch said:**
> I went to **Settings > Advanced > Tor Control **and checked **Use TCP Connection (ControlPort) **with the address **127.0.0.1:9051 **and now is working fine so far.

running Precise (12.04)
        Vidalia 0.2.17
        Qt 4.7.2

I just did the above, did a cold reboot, and still got "tor is not owned by this user". I'm running Vidalia from the desktop, so I'm not root./

Any more ideas?

---

### Post by Enigmapond on 2012-06-07
Yea just purge both vidalia and tor from your system and download the TOR bundle for Linux from the TOR site which runs from a file with no installation and works very well.has it's own browser and have been using it for quite some time with 0 issues.

---

