---
title: "Disabling the CPU stall test"
date: 2012-08-02
forum: General Help
---

### Post by pwabrahams on 2012-08-02
I'm running Kubuntu Oneiric and my system is repeatedly locking up on a CPU stall condition, as indicated by the last entry in syslog.  I doubt if there's any hope of my fixing the cause of the stall, since it involves at a minimum making changes to the kernel code.  But apparently there's a way to override the detection at boot time.  Here's what Documentation/RCU/stallwarn.txt has to say:> 
3	The rcu_cpu_stall_suppress module parameter enables RCU's CPU stall
4	detector, which detects conditions that unduly delay RCU grace periods.
5	This module parameter enables CPU stall detection by default, but
6	may be overridden via boot-time parameter or at runtime via sysfs.
Since the system is unusable once the stall is detected (even CapsLock doesn't work), my best course is probably to disable the detection at boot time.  But how can I do that?  The documentation says that a boot-time parameter will do the trick -- but just how do I do that?

---

### Post by albandy on 2012-08-02
as root:

echo 1 > /sys/module/rcutree/parameters/rcu_cpu_stall_suppress

Then try the system (don't reboot it, simply work with it). If all works fine, set it in sysctl.conf

Also you can try to disable hyper-threading in your BIOS.

---

### Post by pwabrahams on 2012-08-02
I tried what you suggested and it seems to have worked, although only after a reboot.

Since my next step will be a distribution upgrade, I'm hoping that the problem will not reappear.

---

### Post by pwabrahams on 2012-08-02
I discovered that if I install a newer kernel, I have to repeat this procedure.  Is there any way to avoid that?

---

