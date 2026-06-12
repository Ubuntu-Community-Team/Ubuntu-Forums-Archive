---
title: "Multiple OSs and the System Clock"
date: 2010-08-04
forum: General Help
---

### Post by hhh on 2010-08-04
I triple boot with XP on the first partition, sidux on the second and third and Ubuntu on the fourth. sidux controls grub2. When I boot into XP or Ubuntu, my clock gets set ahead 4 hours to UTC time (I'm on Eastern daylight time).

Is there a way for all three OSs to display the right time?

---

### Post by deathadder on 2010-08-04
I find the easiest way to keep my clocks upto date is to use a NTP server to sync the time. 

Ubuntu Link: [https://help.ubuntu.com/9.04/serverguide/C/NTP.html](https://help.ubuntu.com/9.04/serverguide/C/NTP.html)
WinXP Link: [http://csg.trinhall.cam.ac.uk/tips/ntp/winxp](http://csg.trinhall.cam.ac.uk/tips/ntp/winxp)

---

### Post by hhh on 2010-08-04
Thanks for the links. I have them set to sync, but they're still wrong at bootup and I end up manually setting the clock rather than waiting for it to sync.

---

### Post by deathadder on 2010-08-04
It shouldn't take that long to sync.

How are you connecting to the internet? How have you setup NTP?

---

### Post by hhh on 2010-08-04
I had to turn UTC=yes to UTC=no in /etc/default/rcS of both Linux systems. Set the time in XP and now all is well.

Thanks:^)

---

