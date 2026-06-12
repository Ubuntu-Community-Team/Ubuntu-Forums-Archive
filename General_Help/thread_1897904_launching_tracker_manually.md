---
title: "launching tracker manually"
date: 2011-12-20
forum: General Help
---

### Post by pawan.ec on 2011-12-20
Hi,

I want to reduce the boot time of the machine by just not starting the tracker at boot time (as it eats up to much of CPU cycle at boot time "specially tracker-store").

So after booting is done i am making a DBus Connection to the tracker store and it is launched and same for tracker-miner-fs from one of my application.

After some time another application which actually using the Sparql query want another DBUs connection to the tracker-store (via QTSparql) starts and create a DBus connection.

now i see a very strange thing that, there are two tracker-store process running after the second application starts.

Can you guys help me on this.


i tried other stuff like changing the config settign of the tracker, but none of them helps in case of tracker-store as it will be launched on DBus call (correct me if i am wrong)

---

