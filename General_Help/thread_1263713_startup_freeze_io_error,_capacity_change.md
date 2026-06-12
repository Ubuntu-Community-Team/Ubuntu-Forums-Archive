---
title: "startup freeze i/o error, capacity change"
date: 2009-09-11
forum: General Help
---

### Post by nkobel003 on 2009-09-11
When I start up my ASUS EEEPC 1000, it freezes up and will not progress any further. Here are the last few lines when I try 'recovery mode.'

```
sd 1:0:1:0 [sdb] Write Prtect is off
sd 1:0:1:0 [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sdb: detected capacity change from 0 to 32279224320
init: Error parsing configuration: Input/output error
Kernel panic - not syncing: Attempted to kill init!
Dumping ftrace buffer:
(ftrace buffer empty)
```

It has been freezing mysteriously, sometimes even just restarting. The sequence of events to reproduce this was bringing it out of sleep mode, using for various activities, putting back into sleep mode and then it crashed/hung up/froze. I had to perform a hard reset.

Does anyone know how to get beyond this? Perhaps even to skip the boot of sdb and only boot sda? Thanks.

---

