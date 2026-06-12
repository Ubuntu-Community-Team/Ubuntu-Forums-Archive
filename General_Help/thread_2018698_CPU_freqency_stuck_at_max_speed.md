---
title: "CPU freqency stuck at max speed"
date: 2012-07-06
forum: General Help
---

### Post by LxMxFxD on 2012-07-06
Hi all,

I joined this forum some years ago but never really got around to getting acquainted with linux or ubuntu. Now that 12.04 has been released I find it to be quite impressive. Almost as easy to use and user friendly as Windows 7. 

I am having a problem however - my cpu on my laptop is stuck at max (non turbo) speed of 2.53ghz using 64bit 12.04 desktop. Here are some outputs:

[B]#cpufreq-info

current policy: frequency should be within 2.53 GHz and 2.53 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.53 GHz (asserted by call to hardware).
  cpufreq stats: 2.53 GHz:99.99%, 2.53 GHz:0.00%, 2.40 GHz:0.00%, 2.27 GHz:0.00%, 2.13 GHz:0.00%, 2.00 GHz:0.00%, 1.87 GHz:0.00%, 1.73 GHz:0.00%, 1.60 GHz:0.00%, 1.47 GHz:0.00%, 1.33 GHz:0.00%, 1.20 GHz:0.01%  (4)[/B]

I cannot change the cpu freq at all. I can change the governor but its still stuck in the range of "2.53ghz to 2.53ghz". In other words, ondemand, performance, powersave, conservative ALL read as "frequency should be within 2.53ghz and 2.53ghz". Is there a way to fix this? I'd prefer ondemand.

---

### Post by QIII on 2012-07-06
Does your BIOS allow CPU throttling?

---

### Post by LxMxFxD on 2012-07-06
> **QIII said:**
> Does your BIOS allow CPU throttling?

Yes, my cpu is an i5-460m. It shows that it does throttle in the cpufreq-info command. It is just stuck to 2.53ghz to 2.53ghz.

---

### Post by QIII on 2012-07-06
I guess the question is: did you enable CPU throttling in your BIOS?

It should be called SpeedStep for Intel processors, I think.

---

### Post by LxMxFxD on 2012-07-06
> **QIII said:**
> I guess the question is: did you enable CPU throttling in your BIOS?

Of course. It works perfectly in windows.

---

### Post by Redblade20XX on 2012-07-06
Take a look at the jupiter project, 
[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276)

Frequency scaling is built in.

-Red

---

