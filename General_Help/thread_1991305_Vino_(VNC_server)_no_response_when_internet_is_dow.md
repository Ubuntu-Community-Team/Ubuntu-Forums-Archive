---
title: "Vino (VNC server) no response when internet is down"
date: 2012-05-30
forum: General Help
---

### Post by CX23882 on 2012-05-30
I use VNC to connect to my Ubuntu 10.04 server. I only use it across my local network, it is not accessible over the internet nor do I want it to be.

The problem I have is that whenever my internet connection goes down, it becomes impossible to connect to the Ubuntu box via VNC. Other services (SMB, HTTP etc.) are accessible, so it's not a network connectivity issue.

It appears as if Vino, upon receiving an incoming connection, tries to do *something* over the internet.

---

