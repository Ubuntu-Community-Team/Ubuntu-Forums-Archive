---
title: "Transmission says all my ports are closed."
date: 2010-07-16
forum: General Help
---

### Post by The Maxx on 2010-07-16
Hi, I've installed many different versions on Ubuntu, many different times and I've never had a problem with transmission... untill now. I just did a fresh install of Ubuntu 10.04 ( I was already previously using 10.04) and I updated and set up transmission but when I tested the port it said it was closed. This has never happened before.

I tried changing the port about 15 times but it says they are all closed. So I tried opening one...

```
sudo iptables -A INPUT -p tcp --dport 50970 -j ACCEPT
```... but still nothing. I have no firewall running and everything else works fine. Transmission was working before, on the same ports, same version of transmission, and same version of Ubuntu. Nothing has changed.

Does anybody know what's wrong? I can't figure it out :S.

---

### Post by marshmallow1304 on 2010-07-16
Are you behind a router?

---

### Post by The Maxx on 2010-07-16
Thanks for the quick reply :). 

I'm behind a router but the ports are being forwarded and were working fine before. I just tried downloading something and it seems to be working fine  (525 KiB/s right now) despite transmission saying the port is closed...

Do you have any ideas? or should I not push my luck and just leave things the way they are? lol

---

