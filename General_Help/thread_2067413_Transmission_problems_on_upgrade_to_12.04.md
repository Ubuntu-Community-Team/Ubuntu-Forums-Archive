---
title: "Transmission problems on upgrade to 12.04"
date: 2012-10-06
forum: General Help
---

### Post by nooboregon on 2012-10-06
Hi, friends. I recently upgraded my installation from 10.04 (32) to 12.04 (64). I installed Transmission from USS, and it runs alright. It was able to read and verify my torrents/data just fine. However, it is unable to download any new torrents - it won't connect to peers, and AFAICT it will likewise not connect to any peers to seed. I am using port forwarding, and the same port settings as I did in 10.04, and my port is open in Transmission's preferences>network dialog, as well as canyouseeme.org .  I am wondering if somehow I mangled my port blocking OS level, as I used firestarter in 10.04 (ordinarily disabled), but never installed it in 12.04 . I don't have any error messages echoed if I run Transmission from command line. What should I do?

---

### Post by Alfiegerner on 2012-10-21
Exactly the same symptoms here! Transmission thinks the port is ope, connects to trackers and get peers from there and DHT, but fails to download anything. Was working fine until the upgrade.

Anyone have any ideas?  I've turned logging on but no errors are reported.

---

### Post by nooboregon on 2012-10-22
I fixed the issue by ensuring that port forwarding was configured correctly in my modem/router, and then to my personal AP. Likewise, the in/out ports should be different.

---

