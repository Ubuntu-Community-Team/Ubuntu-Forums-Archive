---
title: "Sensors not working &amp; CPU speed control"
date: 2010-02-21
forum: General Help
---

### Post by rem on 2010-02-21
Hello everybody,

I installed Karmic 64-bit on a new Phenom X4 Quad-Core PC. I've replaced the stock CPU cooler with a Cooler Master Hyper TX3, enabled all fan control settings in the BIOS, switched their profiles on “silent”, enabled the “Cool n' Quiet” option as well but my CPU fan is still noisy and seem to be running up to the max number of RPM, thus ignoring BIOS specifications. Besides this I “can tell” there is something wrong with it since even the CPU is on idle or with just the regular browsing, media player operations, PC sometimes freezes or is automatically rebooted .

I installed lm-sensors and went through all the sensors-detect operations (output attached to this post) but it doesn't show anything else but the CPU and HDD temperature which is always 40 Celsius degrees.

I would appreciate any help or advice on properly configuring the sensors detection and maybe help on controlling fan speed and lower the noise. 

Thank you very much!

---

### Post by snkiz on 2010-02-21
Try to get sensor data from a cold start (Shutdown and let the computer cool to room temp.) and while its under load. That will tell you if your sensors are working, because I don't think they are. Your lm-sensor data clearly says there is no driver for your cpu temp. Second your symptoms suggest an overheating issue. When you changed the fan did you use a good quality thermal paste? Did follow the directions to ensure a good thermal bond? Is their good airflow in and around your box? Does this happen with the cover removed? Those are the questions I'd be asking.

---

### Post by rem on 2010-02-21
thank you for your feedback. i did tried to see about the sensors from cold start, under load or idle but it shows the same 40 deg. i used arctic silver 5 thermal paste and installed the cooler according to manufacturer specifications (isn't the first time i'm changing a heatsink + fan). i have 1 case 120 mm fan sucking in cold air and another one of the same size, pushing hot air out. have sirtec 500W power supply with a very efficient fan also and have only 1 HDD so I think a proper ventilation isn't the issue. have to say that freezings and reboots are happening with very low frequency but even so, i don't think that should happen at all. my biggest concern right now is CPU fan control and noise so i think i will agree with you on the driver issue and non-working sensors.

read on some other post that compiling the latest version of lm-sensors would do the trick. have to admit i am not very informed about these drivers and sensors so i'm not keen in installing everything's out there without question so any considered opinion would be deeply appreciated.

thanks.

---

### Post by rem on 2010-02-21
**UPDATE:**

I've compiled and installed lm-sensors, latest version. It doesn't show up anything except the same 40 deg. output, also xsensors is just an empty window so it obviously isn't working for me ... Any thoughts? Thank you.

```
rem@rem:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C
```

---

### Post by rem on 2010-02-21
**UPDATE 2:**

I followed [this tutorial]("http://ubuntuforums.org/showthread.php?t=1319663") (grub editing part) since it was reported as a success, rebooted and run sensors-detect again. Sensors started to work, did pwmconfig and now in normal load, my CPU is silently running at about 1600 RPM. Compared with before, the difference is in almost 2000 RPM so I can report this as a big success.

---

### Post by snkiz on 2010-02-21
Glad to see you worked it out. And learned a valuable lesson brand new hardware can sometimes be too "new".

---

### Post by rem on 2010-02-21
> **snkiz said:**
> Glad to see you worked it out. And learned a valuable lesson brand new hardware can sometimes be too "new".

yes, you are very right :)

---

### Post by psykephaeton on 2010-02-22
Karmic users can install these: 
[https://launchpad.net/ubuntu/+source/lm-sensors-3/1:3.1.2-2/+build/1510409](https://launchpad.net/ubuntu/+source/lm-sensors-3/1:3.1.2-2/+build/1510409) 
to have a lm-sensors compatible with the current Karmic kernel.

Running sensors-detect will now find your fans and voltages.

---

