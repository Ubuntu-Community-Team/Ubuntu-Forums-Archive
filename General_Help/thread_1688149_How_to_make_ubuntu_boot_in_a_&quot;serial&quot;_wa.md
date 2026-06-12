---
title: "How to make ubuntu boot in a &quot;serial&quot; way"
date: 2011-02-15
forum: General Help
---

### Post by rozo on 2011-02-15
Hi,

I would like my ubuntu not to start/boot anything in parallel. It will start longer, but that doesn't matter.
Anyone knows how to do it?

---

### Post by sanderd17 on 2011-02-15
Is There a reason why you want it?

I would suggest to use a single core processor, than everything is serial :-P

---

### Post by rozo on 2011-02-15
I have a problem on an embedded board where usb devices are sometimes not recognized if they are connected before I start the system. If I pull them out and put back again they are always recognized. I tried many things, nothing worked. A friend of mine suggested disabling parallelism for system start.
I have only one core on my system, but that does not matter. If the system starts there are many threads started and each one does their job "parallel" even on one processor.

---

