---
title: "No cpu governor"
date: 2011-11-25
forum: General Help
---

### Post by hexbase on 2011-11-25
Hi,

When i do : > sudo cpufreq-info  i get:

> cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.


Is that a problem?

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-11-25
just means the cpu does not support scaling (or it is disabled in bios)

---

### Post by hexbase on 2011-11-25
Thanks. Now that you remind me, its forced from bios.
Solved

---

### Post by sammiev on 2011-11-25
Please select thread tools and select solved as this may help other people down the road with the same problem. :)

---

