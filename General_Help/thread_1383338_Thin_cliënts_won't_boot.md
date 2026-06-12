---
title: "Thin cliënts won't boot"
date: 2010-01-17
forum: General Help
---

### Post by Génicus on 2010-01-17
At school, we are setting up our 3rd class with a Linux terminal server system, but we experience some problems while doing this.
We have 2 classes on 2 other server running very well, but the new server and clients have some problems while booting up:
We have 23 thin clients in the classroom, when we boot them separately no problems occur.
If we boot them all together (this is the intention), there are 2 or 3 random clients which get a timeout...

We think it is a capacity problem, but that is hard to believe because the server has 8 Xeon cores (2 quad processors) and 4 gigabytes of RAM. The clients are connected to the switch via a 100Mb/s line, the switch is connected to the servers via a gigabit line...

What do you think our problem is? Or how can we avoid the effect?

---

### Post by jamesisin on 2010-01-17
You might monitor the cpu and network activity on the server while this mass-boot is happening (I'm assuming you boot the server ahead of the thin clients).

---

### Post by Leppie on 2010-01-17
sounds a bit like your dns server cannot handle all the requests properly with the current setup.

---

