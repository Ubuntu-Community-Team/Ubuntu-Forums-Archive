---
title: "Root Script at Startup for Power Management"
date: 2011-04-25
forum: General Help
---

### Post by hwttdz on 2011-04-25
I'm trying to enable a few of the powertop suggestions at boot.  My plan had been to put the changes in /etc/rc.local, but it appears possible that some of the changes are happening too early in the boot process to take effect.  Specifically 

echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
and
cd /sys/devices; find . -name link_power_management_policy -print0|xargs --null -n 1 -I{} -t bash -c "echo \"min_power\" > \"{}\""

both work if run with sudo permissions after I've logged in.  Any ideas where to put these such that they'll take effect on boot?  Or can I put a sleep in the rc.local?

---

### Post by bodhi.zazen on 2011-04-25
Adding a sleep in rc.local is easiest.

Second would be to add that command to one of the init scripts, but that is less then ideal as it will likely get over written.

Third would be to write an init script.

Easiest by far, add it to /etc/sysctl.conf

[http://www.go2linux.org/linux/2011/02/introduction-and-how-sysctl-linux-900](http://www.go2linux.org/linux/2011/02/introduction-and-how-sysctl-linux-900)

---

### Post by lithopsian on 2011-04-25
Yes, you can put a sleep in rc.local.  This should be run last or almost last in the boot process and will not slow down anything important.  It might make your bootchart look very long ;)

sched_mc_power_savings should work at any time after the kernel has started.  In fact there is a startup job called procps which will apply these sorts of kernel parameters from a config file during boot.

I'm not sure about the power saving policy changes you're making.  Are they handled by a daemon?

---

### Post by hwttdz on 2011-04-25
It's nice that sched_mc_power_savings should work at any time in the boot process.  It does not.  However it works after I've logged in.  

So saying one wanted to change the value of "/sys/devices/system/cpu/sched_mc_power_savings" using the sysctl method, how would one do that.  From the documentation it appears one can only change values which appear when doing sysctl -a as root (I don't see a power_savings there).

---

### Post by lithopsian on 2011-04-25
If sysctl/procps won't do it then you'll have to stick with your own script.  rc.local is a good place for this and after a sleep should be just fine.  Or you could spawn it off as a task which sleeps for a while and then does the dirty work.

An alternative is to place it in your desktop autostart script, but you would probably need to mess with sudoers to make it work smoothly.  Not ideal but definitely an option.

---

