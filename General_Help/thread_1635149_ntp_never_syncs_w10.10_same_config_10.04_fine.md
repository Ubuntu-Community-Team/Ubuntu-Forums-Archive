---
title: "ntp never syncs w/10.10 same config 10.04 fine"
date: 2010-12-01
forum: General Help
---

### Post by highflux7 on 2010-12-01
Having trouble getting nptd to sync with time server(s) under 10.10.

Using exact same /etc/ntp.conf with 10.04 machines on same network,  have no problem:

root@goober:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*host2.kingrst.c 173.14.47.149    2 u  921 1024  377   36.802    1.347   1.333
+gnu.homeunix.co 193.120.142.71   2 u  889 1024  367    1.242    3.797   1.526
+europium.canoni 193.79.237.14    2 u  631 1024  177  123.002    4.518   1.013


While under 10.10, ntpd seems to see the other hosts but never syncs the time properly:

root@brie:/var/log# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 clock.trit.net  204.34.198.41    2 u   48   64  277   87.405  51899.6 4047.65
 gnu.homeunix.co 193.120.142.71   2 u   49   64  377    0.332  51889.0 3478.55
 europium.canoni 193.79.237.14    2 u   52   64  377  125.846  51856.5 3547.57

ntpdate will query a time server okay under 10.10

Any ideas??

Tks.

---

### Post by highflux7 on 2010-12-01
reboot fixed sync.  ?

---

