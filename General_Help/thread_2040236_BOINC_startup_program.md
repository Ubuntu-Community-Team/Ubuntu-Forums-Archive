---
title: "BOINC startup program"
date: 2012-08-10
forum: General Help
---

### Post by murderd2death on 2012-08-10
Hey, i've got a comp on the side for running extra programs and networking tests. When I'm not using it, i let BOINC run freely. What I want to do is have it automatically come up and run when I log in without be having to go through the dash or anything like that. But when I run the command line 'BOINC' all i get is this

```
travis@manticore4:~$ boinc
10-Aug-2012 13:47:34 [---] No config file found - using defaults
10-Aug-2012 13:47:34 [---] Starting BOINC client version 7.0.27 for x86_64-pc-linux-gnu
10-Aug-2012 13:47:34 [---] log flags: file_xfer, sched_ops, task
10-Aug-2012 13:47:34 [---] Libraries: libcurl/7.22.0 OpenSSL/1.0.1 zlib/1.2.3.4 libidn/1.23 librtmp/2.3
10-Aug-2012 13:47:34 [---] Data directory: /home/travis
10-Aug-2012 13:47:34 [---] Processor: 2 AuthenticAMD AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ [Family 15 Model 107 Stepping 1]
10-Aug-2012 13:47:34 [---] Processor: 512.00 KB cache
10-Aug-2012 13:47:34 [---] Processor features: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
10-Aug-2012 13:47:34 [---] OS: Linux: 3.2.0-27-generic
10-Aug-2012 13:47:34 [---] Memory: 1.83 GB physical, 1.87 GB virtual
10-Aug-2012 13:47:34 [---] Disk: 35.31 GB total, 23.82 GB free
10-Aug-2012 13:47:34 [---] Local time is UTC -4 hours
10-Aug-2012 13:47:34 [---] No usable GPUs found
10-Aug-2012 13:47:34 [---] No general preferences found - using defaults
10-Aug-2012 13:47:34 [---] Preferences:
10-Aug-2012 13:47:34 [---]    max memory usage when active: 938.50MB
10-Aug-2012 13:47:34 [---]    max memory usage when idle: 1689.30MB
10-Aug-2012 13:47:34 [---]    max disk usage: 10.00GB
10-Aug-2012 13:47:34 [---]    don't use GPU while active
10-Aug-2012 13:47:34 [---]    suspend work if non-BOINC CPU load exceeds 25 %
10-Aug-2012 13:47:34 [---]    (to change preferences, visit the web site of an attached project, or select Preferences in the Manager)
dir_open: Could not open directory 'slots'.

```

I've tried searching for a different terminal command that would start BOINC up but alls i get, on the surface, is guides to terminal installations. Any help would be welcome, thanks.

---

### Post by dcstar on 2012-08-10
> **murderd2death said:**
> Hey, i've got a comp on the side for running extra programs and networking tests. When I'm not using it, i let BOINC run freely. What I want to do is have it automatically come up and run when I log in without be having to go through the dash or anything like that.
........

When BOINC is installed from the repositories and set up with projects it runs automatically on boot-up. Just because there is no automatic monitor screen at log in does not mean it is not running,

If you install BOINC from other sources then there is no guarantee that things will be set up correctly.

---

### Post by murderd2death on 2012-08-11
> **dcstar said:**
> When BOINC is installed from the repositories and set up with projects it runs automatically on boot-up. Just because there is no automatic monitor screen at log in does not mean it is not running,

If you install BOINC from other sources then there is no guarantee that things will be set up correctly.

i've checked all my processes and when i try to start it from the command line, and its not there. 

I set it up through the software center, would that do it improperly?

---

