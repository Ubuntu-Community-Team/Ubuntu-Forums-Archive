---
title: "TOR Question"
date: 2010-10-17
forum: General Help
---

### Post by bswalsh on 2010-10-17
I'm sorry if this is an easy question but I'mnew at this. I just installed TOR but get an error that it has ended unexpectedly when I open Vidalia. The log has the following:

Oct 17 18:42:09.770 [Notice] Tor v0.2.2.17-alpha (git-d30d4eb843f12e65). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Oct 17 18:42:09.771 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Oct 17 18:42:09.771 [Notice] Opening Socks listener on 127.0.0.1:9050
Oct 17 18:42:09.771 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Oct 17 18:42:09.771 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Oct 17 18:42:09.771 [Error] Reading config failed--see warnings above.

Does anyone have any ideas? I'm running Ubuntu 10.10. Thanks.

---

### Post by Barriehie on 2010-10-17
See if it's already running, from the terminal:
```

ps aux | grep \/usr\/sbin\/tor
```

You're looking for a line like this:
```

116       3895  0.0  0.6  48560 18444 ?        S    14:20   0:08 /usr/sbin/tor
```

There will also be a line underneath showing where you grepped for it.

---

### Post by bswalsh on 2010-10-18
It's even more annoying now. I can get Tor to run but now Tor Button says that I;m trying to access a proxy that is refusing all connections.

---

### Post by bswalsh on 2010-10-18
Ah, well. I may never find out what's going on, but FoxyProxy works fine.

---

### Post by Barriehie on 2010-10-18
I found Tor Button a pain.  I can see it launch at boot and if I want to not use it I just redirect the browser.

---

