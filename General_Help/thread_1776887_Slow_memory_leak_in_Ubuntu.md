---
title: "Slow memory leak in Ubuntu?"
date: 2011-06-06
forum: General Help
---

### Post by blauendonau on 2011-06-06
When I turn on Ubuntu 10.04, the memory usage on my machine is reported as being around 280 MiB without open windows. However, RAM usage creeps up the longer I use Ubuntu - after a day or two without restarting it can creep up to 350+ MiB, although no additional processes are running, according to the System Monitor. I'm not running any buggy or unstable applications - usually just OpenOffice and Firefox.

I have a lot of RAM and can take it - and I usually restart the computer once in a while - but out of curiosity, I'd like to know where the leak is coming from. Is this sort of thing natural/common?

---

### Post by linuxinstalledfromhdd on 2011-06-06
Have you upgraded to the latest kernel?

---

### Post by blauendonau on 2011-06-06
> **linuxinstalledfromhdd said:**
> Have you upgraded to the latest kernel?

Hm, well, I've updated it every time the Update Manager prompted me to, so I'd say yes. (Unless there are additional kernel upgrades that have to be done manually?)

---

### Post by wildmanne39 on 2011-06-06
> **blauendonau said:**
> When I turn on Ubuntu 10.04, the memory usage on my machine is reported as being around 280 MiB without open windows. However, RAM usage creeps up the longer I use Ubuntu - after a day or two without restarting it can creep up to 350+ MiB, although no additional processes are running, according to the System Monitor. I'm not running any buggy or unstable applications - usually just OpenOffice and Firefox.

I have a lot of RAM and can take it - and I usually restart the computer once in a while - but out of curiosity, I'd like to know where the leak is coming from. Is this sort of thing natural/common?
Hi,that is just ubuntu putting more stuff into memory that you have used since the last time you have shut it down that way you have faster access to it,when you have used enough memory that is needs more then it will clear out the old and make room for the new,that is its way of making the most use of the memory you have to speed up your system.

---

