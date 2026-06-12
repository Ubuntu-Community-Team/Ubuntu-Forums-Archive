---
title: "CPU throttle on boot"
date: 2012-08-31
forum: General Help
---

### Post by BLuFeNiX on 2012-08-31
Hi,

I currently call this script from /etc/rc.local:
```

#!/bin/sh

echo performance | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance | tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
sleep 60
echo ondemand | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand | tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```

Is there a better place to call this script from, so that it runs earlier in the boot process?

Thanks

---

### Post by dodo3773 on 2012-08-31
If I understand what you wrote above it seems like you are trying to use one governor and then switch to another? To answer your question it depends how early in the boot process you are talking about. Is there a rc.multi file in Ubuntu? If so you may want to look in there. If you are just trying to configure a governor it would probably be easier to just use cpufreq-utils or cpupower. If you want earlier then that you can build the governor you want inline in the kernel and / or set the default one there.

---

### Post by BLuFeNiX on 2012-08-31
> **dodo3773 said:**
> If I understand what you wrote above it seems like you are trying to use one governor and then switch to another? To answer your question it depends how early in the boot process you are talking about. Is there a rc.multi file in Ubuntu? If so you may want to look in there. If you are just trying to configure a governor it would probably be easier to just use cpufreq-utils or cpupower. If you want earlier then that you can build the governor you want inline in the kernel and / or set the default one there.

Thanks for the reply. My intention is to max out the CPU speed for the first minute of startup so that the system boots a little faster. 

There does not seem to be a rc.multi file ("locate rc.multi" returned nothing). 

When I used cpufreq-selector I had problems with a race condition (sometimes the governor would not set properly), so I switched to a manual method.

I will look into cpupower and the kernel option.

---

### Post by dodo3773 on 2012-08-31
> **BLuFeNiX said:**
> Thanks for the reply. My intention is to max out the CPU speed for the first minute of startup so that the system boots a little faster. 

There does not seem to be a rc.multi file ("locate rc.multi" returned nothing). 

When I used cpufreq-selector I had problems with a race condition (sometimes the governor would not set properly), so I switched to a manual method.

I will look into cpupower and the kernel option.

Oh okay. I get it now. I do not really think cycling up and down your governor is the best way to speed up your boot process though to be honest. There are a lot of other ways to speed up boot. I would first look into disabling services / daemons you don't need / use. If you really want to speed things up you should experiment with different init systems or init options.  If you automatically boot into your user you can probably get rid of your display manager. If you do not need it you can get rid of your initramfs and compile in all of the modules and filesystems etc.. that you need directly into your kernel. Chasing after a faster boot can be a tedious process. The quickest boot time I have gotten to date was from a gentoo base install with no initramfs and everything built into the kernel.

Edit: I almost forgot. Look into e4rat if you use ext4. Results may vary but it has worked well for me in the past. If you are trying to save time from console -> gui loading then this is almost definitely what you want. Other than that get an ssd if you can afford it.

---

### Post by Doug S on 2012-08-31
which version of Ubuntu are you using?
On my Ubuntu server 12.04, it starts with all CPU's in "performance" mode, and after about 2 minutes or so it switches all CPU's to "ondemand". This was the default, I never changed anything related to this (at least that I am aware of). For specific work, where I wanted, for example, "powersave" mode, I found that had to wait the couple of minutes, or my settings would get clobbered.
 
Edit: On my system S99ondemand is run at run level 2, 3, 4, and 5 executing /etc/init.d/ondemand which will set the CPU's to ondemand mode after 60 seconds.
Same thing on my Ubuntu server 10.10.

---

