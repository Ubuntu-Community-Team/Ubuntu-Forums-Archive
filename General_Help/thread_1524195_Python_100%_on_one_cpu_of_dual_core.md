---
title: "Python 100% on one cpu of dual core"
date: 2010-07-04
forum: General Help
---

### Post by Leppie on 2010-07-04
my laptop fan was blazing like crazy for a while with only firefox and pidgin open. and even after closing firefox, it still continued.
i took a look in htop, and appears that python is sucking 100% of 1 of the two cores all the time. it occasionally swaps core, but it always keeps 1 core completely occupied.
i'm currently on lucid x64.

screenshots of htop and system monitor attached.

---

### Post by oldfred on 2010-07-05
A few weeks ago I wrote a little python program that required a lot of calculations. My mini porcessor app in the top panel showed steady 50% use while program ran. I did not check detail that shows each processor but assumed I max'd out one processor. Python is not multi-threaded as default so it only uses one processor. 

Do you have some python application running away or just taking forever to complete?

---

### Post by Leppie on 2010-07-05
in htop it says something about /usr/share/checkbox/backend
i just found out what is causing this.
i wanted to see what the system testing app does and opened it, but then decided not to start it. however the backend continued as it apparently runs as root.
more info at launchpad about this bug: [https://bugs.launchpad.net/checkbox/+bug/553328](https://bugs.launchpad.net/checkbox/+bug/553328)

---

