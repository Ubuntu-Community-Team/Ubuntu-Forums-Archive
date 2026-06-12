---
title: "What does this CPU history readout mean?"
date: 2010-05-10
forum: General Help
---

### Post by thejakeman on 2010-05-10
It seems that when one core is high, the other is low. It's almost an exact mirror effect right in the middle of the graph... What's up with this?

---

### Post by dcstar on 2010-05-10
> **thejakeman said:**
> It seems that when one core is high, the other is low. It's almost an exact mirror effect right in the middle of the graph... What's up with this?

It simply means that the OS is sharing the load between the available cores.

---

### Post by XCan on 2010-05-10
I believe for some reason the system-monitor will max out one thread on your CPU. But on modern CPUs and OS, the load may not stick to a single core and may switch from time to time, but the total load will still be the same, hence the shape of your graphs.

---

