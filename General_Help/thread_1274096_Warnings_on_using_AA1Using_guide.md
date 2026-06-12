---
title: "Warnings on using AA1/Using guide"
date: 2009-09-24
forum: General Help
---

### Post by reesje on 2009-09-24
Hi all,

I've used the guide found here:
[https://help.ubuntu.com/community/AA1/Using]("https://help.ubuntu.com/community/AA1/Using")
to optimize Ubuntu for Aspire One 110L. However I found a problem in using one of the optimization mentioned in the guide. In the "Increase Battery Life" section. I strongly warn against this line:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

```
I have read somewhere that it only applies to kernels earlier than 2.6.22. Furthermore it ruins the performance on the Atom processor. When this line is not commented out, the processor ondemand scaling doesn't work. The processor is always running at 800MHz. When commented out ondemand scales the processor frequency on demand. I double checked it on two machines several time and every time the result is the same.

Another minor thing, the two lines:
```

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```
It only slows down the boot. Without these lines ubuntu goes into ondemand mode after 60 seconds from boot. It is done this way to speed up the boot time. When these line are added to rc.local, it will go into ondemand immediately, making the boot slower. Once the machine is running it doesn't matter if they are in or out, but the boot time will be longer.

---

