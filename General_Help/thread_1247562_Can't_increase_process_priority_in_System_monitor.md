---
title: "Can't increase process priority in System monitor"
date: 2009-08-23
forum: General Help
---

### Post by Mike_IronFist on 2009-08-23
Well this is odd and annoyingly random.

I've lately been changing process priorities with the system monitor.

Now, for some reason, I can't INCREASE the priorities of any process at all (negative Nice value). I can only DECREASE the priority (positive Nice value). If I try to set the Nice value to ANY negative number at all for any process, the system monitor just closes, while it DOES allow me to set a positive nice value.

Any ideas?

---

### Post by 3rdalbum on 2009-08-23
You need to be root in order to negative-nice a process, but in the past System Monitor has asked for my password in order to do this.

---

