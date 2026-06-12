---
title: "Vidalia ERROR!"
date: 2010-09-17
forum: General Help
---

### Post by crackbuntu on 2010-09-17
installed tor package.
tried to use vidalia for front end and got this error log:


Sep 17 18:15:27.626 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 17 18:15:27.626 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 17 18:15:27.626 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 17 18:15:27.627 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 17 18:15:27.627 [Error] Reading config failed--see warnings above.

please tell me what happened, as u can see i am a beginner (from my beans :D)
or suggesting some other good anonymity method as i recieved a notice not to rely on tor for complete anonymity?

thanks in advance :D
from a remote mountain in the himalayas :)
temperature : -19 degrees. ):P

---

### Post by Soul-Sing on 2010-09-17
> Dont kill a human, Kill a process instead
indeed take a look via top if there is allready a process running like TOR (privoxy?)

---

### Post by vicky.it.bhu on 2010-10-27
Tor is already running, so u gotta kill it

```
sudo killall tor
```

then restart Vidalia

---

