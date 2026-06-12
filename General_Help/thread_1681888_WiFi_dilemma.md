---
title: "WiFi dilemma"
date: 2011-02-04
forum: General Help
---

### Post by noobtolinux on 2011-02-04
Hey all,
As my name suggests, I'm new to ubuntu.  I'm attempting to connect to my wifi, and I've installed wifi radar, but when i attempt to connect there is a loading bar stuck on "acquiring IP address (DHCP).  Does anyone know of a possible problem?

Thanks

---

### Post by 3rdalbum on 2011-02-04
The question I'd have to ask is "Why did you install Wifi Radar" - Ubuntu comes with Network Manager which is a more mature wireless-connection-making program. Have you tried Network Manager? It's towards the right on your top panel.

You could also try going to a terminal and typing "dmesg" after the failed connection attempt; the last couple of lines might give you some clues as to what has gone wrong.

---

