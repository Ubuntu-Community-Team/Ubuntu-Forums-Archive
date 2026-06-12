---
title: "CPU load dropped to unwanted levels after updating 10.04"
date: 2011-06-16
forum: General Help
---

### Post by pekirt on 2011-06-16
Hi everyone,

First off, I don't know whether this is the right place to post this. I'd appreciate if the good folks here would point to the right sub-forum.

We're running Ubuntu 10.04 LTS. Due to the nature of our work, we won't upgrade from LTS releases until a new one is available.

We're cooking our CPUs with numerical work done for research purposes. Thus, 100% CPU load on all CPU cores 24/7 for weeks at a time is normal, and required. However, after doing some updates at sometime in the first week of June 2011, top shows 75.1% niced, 24.9% idle in all our cores. It wasn't so before the upgrade. The nature of the numerical work is such that it should always top the CPUs to 100%. This is seen in both pentium and athlon 1100XT chips. I could give you more details on our computers, but since this happened across multiple platforms, I don't think that's it.

Is it possible that the g++ compiler changed and is responsible? Our numerical code is in C++, after all. If not, what's going on?

I'd like to repeat that we *WANT* high CPU loads.

Thanks everyone,

Baris

*************
My kernel version:

$ cat /proc/version
Linux version 2.6.32-31-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011

my top version:

$ top -v
    top: procps version 3.2.8
usage:    top -hv | -bcisSH -d delay -n iterations [-u user | -U user] -p pid [,pid ...]

---

