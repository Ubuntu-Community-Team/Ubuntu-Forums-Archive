---
title: "Ubuntu crashes, log attached"
date: 2012-01-21
forum: General Help
---

### Post by ygoe on 2012-01-21
Hi,

My Installation of Ubuntu 11.10 on an ALIX 3d3 box basically works well, but after a few days of use, the system crashes. I hat the serial console attached for the last few days and have seen the attached output. Unfortunately I didn't have file logging enabled and the line buffer was way too small for the continuous console messages. But I hope the cut from the middle (until I plugged out the power) is useful, too.

I guess it's some memory allocation problem, but I'm not sure why. I am monitoring memory usage and it looks good. The machine has 256 MB RAM and in operation, normally 30 MB are used, the rest is filled up with caches and buffers.

What's going on here?

Hm, I cannot attach anything useful to this forum. (log/7z is invalid and txt is too large) See my log file here: [http://unclassified.de/tmp/putty-alix-com7-error-20120121.log](http://unclassified.de/tmp/putty-alix-com7-error-20120121.log)

Edit: I forgot to say that the running SSH connection was closed and I could not connect to it either. I have now made a memory usage plot. The missing time is when it wasn't working today. [http://unclassified.de/tmp/alix-memusage.png](http://unclassified.de/tmp/alix-memusage.png)

---

### Post by ygoe on 2012-01-21
Another crash, in less than a day. Here's another complete serial console session. This time, there was no continuous stream of error messages, but no programme could be started, every time "segmentation fault". I cannot find out anything about the system's state if it just fails at everything. Where should I start to search?

[http://unclassified.de/tmp/putty-alix-com7-error-20120121b.log](http://unclassified.de/tmp/putty-alix-com7-error-20120121b.log)

---

