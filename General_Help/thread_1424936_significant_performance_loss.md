---
title: "significant performance loss?"
date: 2010-03-08
forum: General Help
---

### Post by djyoung4 on 2010-03-08
Ok i booted up this morning and I am noticing a very significant performance loss.  Last night everything was great but this morning everything is running very slow and it is very sporadic.  I have already restarted.  any suggestions

---

### Post by Techsnap on 2010-03-08
Have you checked the system monitor to look at if anything is using up resources?

---

### Post by djyoung4 on 2010-03-08
> **Techsnap said:**
> Have you checked the system monitor to look at if anything is using up resources?

how can i check it.  Sorry i usually have conky to watch my system but I have a very minimalist one right now.

---

### Post by efflandt on 2010-03-08
Some terminal commands can help you tell some things.

**free -m** can tell how much memory is actually being used besides buffers and cache, and whether swap is being used.

**top** can give various info about processes using the most cpu time.  If load average climbs while cpu percentage is low, processes may be building up doing indexing or waiting to write to disk.  **q** quits.

**ps aux | less** can let you look through all processes to see which processes are using a high percentage of memory, either doing something or sleeping.  Maybe something is going into a race condition or becoming a zombie.

---

