---
title: "Cpu frequency governor stuck"
date: 2011-02-04
forum: General Help
---

### Post by JustinR on 2011-02-04
Hey everybody, I've seen other people with this problem but no solution.

I'm using the latest kernel and after I boot up my computer the cpu governor changes from the fastest setting (2ghz) to the slowest setting (800mhz), and gets stuck there. Theres no obvious way to change the setting, the gnome applet to change the cpu frequency doesn't work - I've also tried to change the setting manually through the /sys/ directory but to no avail.

There was a suggestion to fallback on an older kernel, but my older kernels suffer from the same bug.

Does anybody have any ideas? I can provide more information on request.

Thanks.

Edit: sorry I forgot to post computer specifications.

Dell Inspiron 1720 with an Intel 2 Core Duo @ 2 ghz.

---

### Post by cascade9 on 2011-02-04
It will stay there unless you put the system under some load. 

Exactly how much load you need to kick cpufreq up to the next speed depends on your system.

---

### Post by JustinR on 2011-02-04
> **cascade9 said:**
> It will stay there unless you put the system under some load. 

Exactly how much load you need to kick cpufreq up to the next speed depends on your system.

Thanks for the reply, but the cpu governor is set to performance, not on demand. Even though it's set at performance, it reports it at 800mhz.

---

### Post by TBABill on 2011-02-04
To change it manually you could try ```
sudo cpufreq-set --governor performance
``` and that will kick it to 100% full time.

---

### Post by TBABill on 2011-02-04
Please note that you MAY have to do it for each CPU on the system. They are in order and if you have a dual core your system may report that you have 4 processors....all that's hardware dependent of course. Mine reports 4 CPU's for my Intel Core i3 so you'd possibly have to do ```
sudo cpufreq-set cpu0 --governor performance
``` and then do cpu1, cpu2, cpu3. Depends on your setup but worth a shot if the single setting previously posted doesn't quite get you there.

---

### Post by JustinR on 2011-02-05
Thanks for the reply.

I tried both codes you suggested, both cpu governors are set at performance like before, but there still only operating at 800mhz.

---

### Post by dino99 on 2011-02-05
with synaptic, remove/purge then reinstall cpufrequtils & libcpufreq0, and check the bios settings too.

---

### Post by JustinR on 2011-02-05
Thanks for the reply,

Some more updates on this:
The cpu governors work fine at startup. I can switch from different governors but after a minute or so, no matter which governor I'm in, eg. Performance, the cpu speed reverts to 800mhz and both cpus are maxed out by an unknown process - my computer gets very sluggish and unusable.

I purged both of the packages and restarted and that didn't work. BIOS settings were fine.

---

### Post by JustinR on 2011-02-05
After fiddling around some more, I'm trying to change the speed manually again.

Changing the governor (/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor) with this command:
```

echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
This runs successfully but doesn't actually change the cpu freq, although the governor is at performance-the freq is still at 800mhz.

So then I tried to change the frequency manually with this code:
```

echo 2001000 | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq

```

But it returns this:
> 
tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur/governor: Permission denied

I ran the command again in a root terminal but got the same message. I also tried the file "cpuinfo_cur_freq" but that didn't work either.

So does anybody have any ideas? Thanks.

---

### Post by mc4man on 2011-02-05
You may want to try to identify what's pushing your cpu(s) to 100%, run top in a terminal or install htop and run that.

One thing to consider about being locked at 800 - if at any point your cpu temps reach the scale down threshold (overheating), then you most likely will be scaled down to  800 and be locked there till a reboot even if the temps go back to normal or thereabouts.

You may want to find a way to monitor the cpu temps right  after boot in a fairly constant manner (every few  seconds or so) and see if you reach that point (probably around 99C

Depending on hardware and kernel there would be various ways to do, see if this returns a reading
```
cat /proc/acpi/thermal_zone/THM/temperature
```
If so then an app named computertemp will work ok, it can be added as a panel applet and better, configured to write out to a log
If above doesn't work then browse and ck. path or install the applet and see
To configure  - add to panel, r. click > preferences - screen
(if computertemp doesn't work then you'll need to explore other ways - keep in mind you need to get readings before you scale to 800, not after

---

### Post by JustinR on 2011-02-06
I did try top earlier but nothing was using much CPU, but the CPU's were always maxed out.

Process' like gnome-multiload-applet and gnome-system-monitor, apps that can change and monitor the CPU were always causing heavy load, especially after changing the CPU scaling - they would stop responding.
No errors were reported in DMESG.

Also, my CPU temperature on average is 69C - far below what it can handle, and it still can't be set above 800MHZ.

Thanks for the reply though.

---

### Post by ddrpl on 2011-02-06
I have the same problem with my Lenovo T61. The governor is stuck at 800 Mhz when my T61 is connected to docking station.

I think this error is kernel related because governor works fine for me on older kernels (for eg. 2.6.31-11 RT).

---

### Post by L_V on 2011-02-06
I had the same problem with Maverick on a Dell Latitude D600 stuck at 600MHz after some minutes of normal behavior.
The only solution I found: install Debian.

---

### Post by JustinR on 2011-02-06
A complete reinstall with the kernel that came on disk did not solve the problem - so it could be a hardware issue. Ugh...

I'll give a different distribution a try and maybe even Windows before I try to reseat the cpu & cpu heat sink.

Edit: I haven't tried a different distro/Windows but it's been running fine for the past twenty minutes so far...

---

