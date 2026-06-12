---
title: "Can't Shutdown"
date: 2010-01-03
forum: General Help
---

### Post by Ansraliant on 2010-01-03
Hi everyone!. I'm having a problem shutingdown my ubuntu 9.10.
When I shutdown, it hangs after "Deactivating swap". It doesn't say fail or ok, just hangs there. Keyboard is still working.
Hope you can help me.
Thanks for everything.

PS: Sorry for my bad english, haven't practice it in a while.

---

### Post by Ansraliant on 2010-03-15
Solved the problem. There was missing the link to the system function halt in the folder /etc/rc0.d. That's why it just hanged.
I copied the link from a live cd to my ubuntu partition, and it worked just fine.

---

