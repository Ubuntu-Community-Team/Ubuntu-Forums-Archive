---
title: "Start Redshift at Startup?"
date: 2012-04-07
forum: General Help
---

### Post by Thrashrokz33 on 2012-04-07
Ubuntu 11.10. My Redshift program isn't running at startup, even though I have it set under the "startup applications preferences" under the power button icon in the corner.

The command I have set is:

sleep 5 && redshift

I'm assuming at startup, this should wait five seconds to execute, and then starts the redshift program. It doesn't, though. I always have to go into terminal and type "redshift" for it to start.

Any ideas to why it isn't working?

---

### Post by dcstar on 2012-04-07
> **Thrashrokz33 said:**
> Ubuntu 11.10. My Redshift program isn't running at startup, even though I have it set under the "startup applications preferences" under the power button icon in the corner.

The command I have set is:

sleep 5 && redshift

I'm assuming at startup, this should wait five seconds to execute, and then starts the redshift program. It doesn't, though. I always have to go into terminal and type "redshift" for it to start.

Any ideas to why it isn't working?

The Startup Applications is **not** a shell environment.

Create a proper script and run that.

---

### Post by jim_deadlock on 2012-04-07
There is a bug report about this, at the moment the only thing to do is start it twice then it runs fine. Put it in your startup progs and then also run it manually from the dash.

---

