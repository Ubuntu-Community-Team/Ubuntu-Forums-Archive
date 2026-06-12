---
title: "VPN Connect from Terminal/Automatically Reconnect"
date: 2009-11-03
forum: General Help
---

### Post by sollicity on 2009-11-03
My network connection in Ubuntu is rather unstable, and has a tendency to break at times.
(This is most likely a problem with the router, and I don't think it can actually be fixed in ubuntu.)

I have a script running that will automatically reconnect the network, should it break.
It doesn't, however, reconnect using Network Manager; the tray icon will still show disconnected.

Now my problem is that I'm running a VPN connection to Relakks, which will break with the internet connection. I have to find a way to reconnect the Relakks connection when this breaks.

I don't know exactly what information will be required for anyone to help me, so please specify this.

I have tried a couple of ubuntu help threads, but none actually worked. 

So ehm... please help?

---

### Post by Giblet5 on 2009-11-03
You *could* try kvpnc (a KDE vpn client). It's a front-end to openvpn and it allows you to specify the IP address of a remote system to periodically check that's only accessible through your tunnel. You also specify how often to test. If the test fails, kvpnc will disconnect and reconnect (often, in less than one second).

You might also want to talk with the geeks at your ISP. It's possible that their router is dropping your connection due to misconfiguration on your, or their, end.

---

