---
title: "process killing cpu"
date: 2012-09-11
forum: General Help
---

### Post by matimont on 2012-09-11
Hi,

Today I was by chance looking at my VPS cpu usage and noticed 1 site was killing resources, see this:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7961 siteweb  20   0  198m  39m 6660 R 20.3  3.9   1:06.88 php5-cgi
 9985 siteweb  20   0  190m  31m 6656 S 17.3  3.1   0:21.00 php5-cgi
 7976 siteweb  20   0  190m  31m 6676 S 16.9  3.1   1:12.19 php5-cgi
 8288 siteweb  20   0  190m  31m 6660 S 16.6  3.1   1:01.52 php5-cgi
 9313 siteweb  20   0  190m  31m 6676 S 16.6  3.2   0:41.30 php5-cgi

why I see multiple processes for the same site? and why it may be that high CPU usage?

thanks,

---

### Post by matimont on 2013-01-04
Help.. :)

---

### Post by rnerwein on 2013-01-04
> **matimont said:**
> Hi,

Today I was by chance looking at my VPS cpu usage and noticed 1 site was killing resources, see this:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7961 siteweb  20   0  198m  39m 6660 R 20.3  3.9   1:06.88 php5-cgi
 9985 siteweb  20   0  190m  31m 6656 S 17.3  3.1   0:21.00 php5-cgi
 7976 siteweb  20   0  190m  31m 6676 S 16.9  3.1   1:12.19 php5-cgi
 8288 siteweb  20   0  190m  31m 6660 S 16.6  3.1   1:01.52 php5-cgi
 9313 siteweb  20   0  190m  31m 6676 S 16.6  3.2   0:41.30 php5-cgi

why I see multiple processes for the same site? and why it may be that high CPU usage?

thanks,
hi
20% isn't much for a php5-cgi ( i think it's in user mode - see top third line (Cpu)
cheers

---

### Post by matimont on 2013-01-04
Well, actually the screenshoot may habe been incorrectly pasted.

There was one php5-cgi at 97% during more than 30 minutes.

Thanks!

---

