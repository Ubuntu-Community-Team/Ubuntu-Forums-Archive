---
title: "Performance issue"
date: 2011-04-26
forum: General Help
---

### Post by biodude on 2011-04-26
My desktop is a core i7 930 @ 2.8GHz, running Ubuntu Desktop 10.10 and the cpufreq governor is set to "performance".

When I run this loop I get the following times:

Ubuntu 10.10 (installed, cpufreq=performance (same for ondemand)):

$ time perl -e 'for($i=0;$i<1e7;$i++){}' 

real    0m0.937s
user    0m0.920s
sys    0m0.010s


Ubuntu 11.04 beta (live cd, default cpufreq governor)

$ time perl -e 'for($i=0;$i<1e7;$i++){}' 

real    0m0.935s
user    0m0.918s
sys    0m0.010s


Ubuntu 10.04  (live cd, default cpufreq governor)
 
 $ time perl -e 'for($i=0;$i<1e7;$i++){}' 
 
 real    0m0.525s
 user    0m0.510s
 sys    0m0.010s
 
The cpus either run at 2.8 or 1.6 GHz (from /proc/cpuinfo). 
cpu MHz        : 2794.000
cpu MHz        : 1596.000


These times are proportional to 1.6 and 2.8 GHz. I think that something in the software (after ubuntu 10.10) is preventing the CPUs to run at full speed. 

Any ideas?
Thanks!

---

