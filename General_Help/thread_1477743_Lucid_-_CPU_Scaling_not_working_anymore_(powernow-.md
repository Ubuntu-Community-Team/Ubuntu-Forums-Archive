---
title: "Lucid - CPU Scaling not working anymore (powernow-k8)"
date: 2010-05-09
forum: General Help
---

### Post by krul on 2010-05-09
In Lucid I cannot get CPU scaling to work anymore, in previous Ubuntu releases this was not a problem with the same hardware (AMD Phenom 9500 Quad).

I used to load module 'powernow-k8' and 'powernowd' to make it work, but it seems 'powernow-k8' is not available in Lucid.

Anyone who has cpu scaling working in Lucid?

---

### Post by dcstar on 2010-05-09
> **krul said:**
> In Lucid I cannot get CPU scaling to work anymore, in previous Ubuntu releases this was not a problem with the same hardware (AMD Phenom 9500 Quad).

I used to load module 'powernow-k8' and 'powernowd' to make it work, but it seems 'powernow-k8' is not available in Lucid.

Anyone who has cpu scaling working in Lucid?

Works fine for me. There are no modules to load as they are built into the kernel, and when the powernowd package installs it sets thing up.

---

### Post by krul on 2010-05-10
When I execute powernowd I get the following error:


```
powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 4 scalable units:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu

```

It seems I have still to load powernow-k8 module, right?

---

### Post by philinux on 2010-05-10
I've not done anything just added the applet to top panel.

Seems to work fine.

---

### Post by -humanaut- on 2010-05-10
> **philinux said:**
> I've not done anything just added the applet to top panel.

Seems to work fine.

Same for me. 

Maybe it's an installation issue?

---

### Post by krul on 2010-05-11
Strange, I also added the applet but every reboot it gives an error CPU scaling not supported. But in Karmic and previous versions it was working (after loading in the required modules).

What do you mean with installation issue? I did a fresh install of Lucid. Are you using the same hardware?

---

### Post by dcstar on 2010-05-11
> **krul said:**
> Strange, I also added the applet but every reboot it gives an error CPU scaling not supported. But in Karmic and previous versions it was working (after loading in the required modules).

What do you mean with installation issue? I did a fresh install of Lucid. Are you using the same hardware?

The applet is **only** a monitor, you can load it as many times as you want but it will only report on what the system provides.

Look in the syslog file for the scaling messages at boot time.

---

### Post by krul on 2010-05-11
I found this in the syslog:

```
May 11 08:54:44 quad kernel: [    0.889784] powernow-k8: Found 1 AMD Phenom(tm) 9500 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
May 11 08:54:44 quad kernel: [    0.889794] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
May 11 08:54:44 quad kernel: [    0.889795] [Firmware Bug]: powernow-k8: Try again with latest BIOS.

```

I think I am already running the latest BIOS version. I have a Asus M3A motherboard.

---

### Post by krul on 2010-05-11
Ok, I googled on the error and found out that most probably 'Cool 'n Quit' is disabled in the BIOS. However, I remember I have enabled this while back and haven't touch it since, I just check and indeed this was disabled!
Not sure how. But now cpu scaling is working!

Thanks for pointing out to look at the syslog.

---

### Post by dcstar on 2010-05-11
> **krul said:**
> Ok, I googled on the error and found out that most probably 'Cool 'n Quit' is disabled in the BIOS. However, I remember I have enabled this while back and haven't touch it since, I just check and indeed this was disabled!
Not sure how. But now cpu scaling is working!

Thanks for pointing out to look at the syslog.

Check your CMOS battery still works after you power off your PC (remove the power cable) for at least 10 minutes.

---

### Post by krul on 2010-05-12
> **dcstar said:**
> Check your CMOS battery still works after you power off your PC (remove the power cable) for at least 10 minutes.

Sounds plausible. I will check the battery.

---

