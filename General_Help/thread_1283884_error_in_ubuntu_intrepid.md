---
title: "error in ubuntu intrepid"
date: 2009-10-06
forum: General Help
---

### Post by lawaris on 2009-10-06
i am using ubuntu 8.10.But due to some errors,my native system does not open and root terminal opens up telling me to do manual fsck.What to do now?

---

### Post by utnubuuser on 2009-10-06
Do what the system suggests. > But do it from a liveCD, because some disk utitilies can damage mounted file systems.

One of the easiest checks you can do is to launch the liveCD, wait till the desktop loads, then go to System>>Administration>>Partition Editor

Highlight a partition, rick-click and choose "Check"



also check > man fsck in a terminal to get more info on the fsck utility and it's arguments

0,

---

