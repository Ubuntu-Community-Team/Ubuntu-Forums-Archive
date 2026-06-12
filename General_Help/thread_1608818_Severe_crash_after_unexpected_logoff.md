---
title: "Severe crash after unexpected logoff"
date: 2010-10-29
forum: General Help
---

### Post by crashflow on 2010-10-29
Today my system, a Samsung R41 laptop, suddenly logged itself out of Kubuntu 10.04 after 11 hours of fine operation.

When I restarted the system, the following happened:

- After the first hard reset, the harddisk loaded for a while, then stopped. The screen remained black.
- After the second hard reset, the load process stopped and I was informed that GART did not load due to some ASIC bug.
- After the third hard reset, I could log in to KDE. I was informed that two audio components had been removed and the drivers could be deleted permanently. I disagreed and restarted the system.
- After the fourth new startup, network access was gone. The reason was that the file NetworkManager.state in the directory var/lib/Networkmanager contained the entry EnableNetworking=false.

Any ideas why all of this happened at once?

At the time of the crash, I was running Firefox version 3.6.12, Amarok version 2.3.0 and streamripper 1.64.6 in a bash shell.

crashflow

---

