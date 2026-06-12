---
title: "CPU fan goes at max speed after suspend"
date: 2010-06-19
forum: General Help
---

### Post by s.v.z on 2010-06-19
Hi everyone! I`ve got an hp6735b laptop with Lucid Lynx(2.6.32-22-generic). After the system wakes up from Standby, the CPU fan keeps going at max speed, no matter what the temp is, and never slows down until reboot.

---

### Post by iponeverything on 2010-06-19
run "top" in a terminal after you wake-up to see what process is running away.

---

### Post by s.v.z on 2010-06-19
What do you mean by "running away"? If you mean this:  *some process loads cpu -> temp rises -> fan goes fast, *- then it's not the reason.

The fan goes at max even when the cpu is 90% idle and ice-cold.

---

### Post by iponeverything on 2010-06-19
Has the issue always been there or is it new.

---

### Post by iponeverything on 2010-06-19
found this in launchpad, it may be your bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/77370](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/77370)

---

