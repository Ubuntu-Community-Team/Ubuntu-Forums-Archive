---
title: "Having Problems with TOR/Vidalia in Ubuntu Meerkat Maverick"
date: 2011-09-17
forum: General Help
---

### Post by spawnrun on 2011-09-17
Hey y'all,
  I'm pretty new to linux and I use this forum a lot; it's a real lifesaver!  Anyway, I've installed TOR and Vidalia via command line, following directions found on google.  Now, everything seemed to intsall ok, but when I try and start Vidalia, I get and error saying that TOR exited unexpectedly.  When I look in the advanced log, it says:

Sep 17 12:01:37.483 [Notice] Tor v0.2.3.4-alpha (git-9986082fc4414b7d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Sep 17 12:01:37.494 [Notice] Read configuration file "/home/sean/.vidalia/torrc".
Sep 17 12:01:37.495 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 17 12:01:37.495 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 17 12:01:37.495 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 17 12:01:37.495 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 17 12:01:37.495 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 17 12:01:37.495 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 17 12:01:37.495 [Error] Reading config failed--see warnings above.

Now, I've been all over here and google and I see that this is a fairly common problem, but I haven't found a solution that works, or that I can understand.  Anyone?

---

### Post by spawnrun on 2011-09-19
Ok, a little update:

  I killed TOR using the command
      sudo killall tor

This seemed to work, as I was able to connect to the TOR network (according to Vidalia, anyway).  BUT, when I try this page, [https://check.torproject.org/](https://check.torproject.org/), it says that I am not using TOR.  What did I do wrong?

---

### Post by foureyesboy on 2011-09-19
After Vidalia is run successfully, did it fire up a browser automatically?  Or were you using your preferred browser?

I took a different approach and didn't go through the installation steps.  I just run start-tor-browser under tor-browser_en-US folder inside my home and it will fire up the tor browser automatically.

If you use other preferred browser after running Viladia, you'll have to configure individual browser and point the corresponding proxy setting to SOCKS at localhost:9050.

---

### Post by NoNameWill on 2011-09-19
I had the same problem with vidalia. I just use tor. Also is polipo configured correctly?

---

