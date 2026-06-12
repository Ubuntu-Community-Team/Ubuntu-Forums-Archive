---
title: "high system load"
date: 2012-06-27
forum: General Help
---

### Post by vcamel on 2012-06-27
I have high system load on my Ubuntu 10.04.3 LTS for long time. I cannot find any running process. 
  Load sometimes growing up after I unmount  LVM snapshot  and remove it.
  I found that I have number of udevd processes in high-priority uninterruptible sleep state.
  # uptime
   13:23:39 up 21 days,  6:20,  2 users,  load average: 6.19, 6.20, 6.18
  # ps auxww | grep udev
  root      8025  0.0  0.0  16960   432 ?        D<   Jun06   0:00 udevd --daemon
  root      8027  0.0  0.0  16960   308 ?        D<   Jun06   0:00 udevd --daemon
  root      8408  0.0  0.0  16960   372 ?        D<   Jun06   0:00 udevd --daemon
  root      8411  0.0  0.0  16960   480 ?        D<   Jun06   0:00 udevd --daemon
  root      8412  0.0  0.0  16960   416 ?        D<   Jun06   0:00 udevd --daemon
  root     27207  0.0  0.0  16960   484 ?        D<   Jun10   0:00 udevd –daemon
   
  Does anybody have idea why this is happened and how to bring load to normal?

---

