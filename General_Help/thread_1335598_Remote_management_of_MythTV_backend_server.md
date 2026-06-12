---
title: "Remote management of MythTV backend server"
date: 2009-11-23
forum: General Help
---

### Post by allanlewis on 2009-11-23
I have a MythTV backend that is generally used for a few hours in the evening, but rarely during the day. Therefore, it's in suspend most of the time, to save power, and I've worked out how to get my frontends (a desktop and a laptop) to wake up the backend using the "wakeonlan" command. I've also worked out how to suspend the system remotely via ssh. (I've written a script that first stops "mythtv-backend" and them runs "pm-suspend".)

I'd like to integrate this into MythTV, but I don't want to stop/suspend the backend if another frontend (possibly the one running on the same machine as the backend) is connected. Is there any way I can say to my server, "If a client is connected, or if the local frontend is running, stay awake, otherwise suspend"? (By "suspend", I really mean, "run an arbitrary script that requires root privileges.) I'd like this "question" to be asked whenever a frontend is closed, so that the backend will go into suspend when the "last" frontend disconnects, and wake up using "wakeonlan" when another one tries to connect.

I hope that all makes sense! Any help will be greatly appreciated.
---
Background: My backend is a desktop running Karmic (64-bit) and is connected by wire to my Internet router. My frontends are another desktop and a laptop, both connected to the same router by Wi-Fi, and both running Karmic 32-bit.

---

