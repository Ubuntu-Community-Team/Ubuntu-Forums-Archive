---
title: "OMP_NUM_THREADS or NCPUS value (8) is invalid"
date: 2012-09-03
forum: General Help
---

### Post by AC_Soaring on 2012-09-03
I am installing a multi-threaded application (wrf) on an I7-920 based Ubuntu server system.  I can see all 8 CPU's from the monitor, but I can only keep 4 of them busy.  When I tell the application it has 8 cpu's available I receive the following error "OMP_NUM_THREADS or NCPUS value (8) is invalid".

This is true for any value of OMP_NUM_THREADS greater than 4.  The application runs with a value of 4, but half the cpu's are idle.

Thank you,

Alan

---

### Post by gordintoronto on 2012-09-04
Your I7-920 is a quad-core CPU.
[http://ark.intel.com/products/37147/Intel-Core-i7-920-Processor-(8M-Cache-2_66-GHz-4_80-GTs-Intel-QPI](http://ark.intel.com/products/37147/Intel-Core-i7-920-Processor-(8M-Cache-2_66-GHz-4_80-GTs-Intel-QPI))

It supports multi-threading, but it has four CPUs.

---

### Post by AC_Soaring on 2012-09-04
Gord:

I'd agree except all 8 threads are shown in monitor.  The 4 that are not being used on the I7 for wrf sometimes show low usage (10 - 12%) by other processes. I have tried setting OMP_NUM_THREADS to 8 and leaving ncpus at 4.

- Alan

---

### Post by AC_Soaring on 2012-09-05
I've also checked the dmesg output and it matches the monitor display; shows as starting 8 cpu's.

- Alan

---

### Post by AC_Soaring on 2012-09-06
I have learned of a Fedora user running the same software with 4 physical CPUS and hyperthreading (grep "core id" /proc/cpuinfo | sort -u | wc -l"  reports 4).  He achieves 8 cpus at 98%.

Is this issue limited to Ubuntu?

- Alan

---

### Post by AC_Soaring on 2012-09-09
Solved - The version of the executable I was running was capped at 4 cpu's.

- Alan

---

