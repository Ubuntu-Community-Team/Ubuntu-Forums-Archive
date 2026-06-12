---
title: "Killing terminal service client remotely"
date: 2011-05-03
forum: General Help
---

### Post by bartonski on 2011-05-03
I'm running 10.04 at work. On that machine, I left myself logged in to a windows box via the terminal service client.

I'm now working from home, trying to connect to the same windows box via RDP, but the windows server won't allow multiple connections for a single user via RDP, so I want to kill the terminal server running from my Linux box... unfortunately, every time I kill it, it respawns after 10 or 20 seconds. Is there a way to kill it and make it stay dead?

Note that I've only got ssh access to the Linux box... yes, I know that I can do port forwarding through ssh, so theoretically I could do something with the GUI, but I would prefer to control this via command line only... less fiddling around.

---

### Post by DaithiF on 2011-05-03
Hi,
The rdesktop client is run by a wrapper 'tsclient' program that watches for terminations of its child process and respawns after (on my system) 30 seconds.

So to prevent respawning kill both the rdesktop and tsclient programs
```
killall -9 rdesktop tsclient
```

---

