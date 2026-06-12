---
title: "How accurate are the coretemp temperature sensors in linux?"
date: 2009-10-01
forum: General Help
---

### Post by ownaginatious on 2009-10-01
Right now I use conky to display the temperature of my CPU among other things. One thing I've noticed though is that the temperature being reported seems ridiculously high (pushing 60 degrees Celsius). When in windows, however, I stay around high 30s to low 40s.

Could it actually be a power management problem in linux causing my processor to overheat, or is the coretemp program for measuring temperature simply inaccurate? If the latter, is this possible to fix?

Thanks,

Dillon

---

### Post by vishy1618 on 2009-10-01
Look in /proc/acpi/thermal_zone for any files. Read those files. If they differ then it must be a bug in the program.

---

### Post by dcstar on 2009-10-01
> **ownaginatious said:**
> Right now I use conky to display the temperature of my CPU among other things. One thing I've noticed though is that the temperature being reported seems ridiculously high (pushing 60 degrees Celsius). When in windows, however, I stay around high 30s to low 40s.

Could it actually be a power management problem in linux causing my processor to overheat, or is the coretemp program for measuring temperature simply inaccurate? If the latter, is this possible to fix?


Each CPU family can provide temp data in various ways, and the software that interprets that data needs to know exactly what formula to use to provide accurate output. Unfortunately CPU vendors seem to support Windows more than Linux so there can be discrepancies.

My own AMD Athlon CPU does not report accurate temp output in Linux because when AMD changed the "Core" from the previous model they also changed the temp output - and the Linux package does not differentiate between the original and newer (Brisbane) core CPUs.

Be also aware the CPU temp is directly affect by system load and correctly set up power saving, so if you are pushing your CPU harder in Linux and/or you do not have the CPU throttling back when idle then it will run hotter.

---

### Post by ownaginatious on 2009-10-02
> **vishy1618 said:**
> Look in /proc/acpi/thermal_zone for any files. Read those files. If they differ then it must be a bug in the program.

Hmm, there is nothing located under the directory /proc/acpi/thermal_zone

> **dcstar said:**
> Each CPU family can provide temp data in various ways, and the software that interprets that data needs to know exactly what formula to use to provide accurate output. Unfortunately CPU vendors seem to support Windows more than Linux so there can be discrepancies.

My own AMD Athlon CPU does not report accurate temp output in Linux because when AMD changed the "Core" from the previous model they also changed the temp output - and the Linux package does not differentiate between the original and newer (Brisbane) core CPUs.

Be also aware the CPU temp is directly affect by system load and correctly set up power saving, so if you are pushing your CPU harder in Linux and/or you do not have the CPU throttling back when idle then it will run hotter.

Hmm, I don't think I'm pushing my CPU excessively. I rarely have processor intensive programs open.

---

### Post by MaxIBoy on 2009-10-02
Depends on how expensive the processor is. If it's cheap, the numbers are pretty well known. If it's expensive, no one's brave enough to find out... 

(Actually, I have no clue. But in my experience, even if it's inaccurate, the number is still useful for figuring out whether or not to ease up the overclocking or something.)

---

### Post by ownaginatious on 2009-10-02
> **MaxIBoy said:**
> Depends on how expensive the processor is. If it's cheap, the numbers are pretty well known. If it's expensive, no one's brave enough to find out... 

(Actually, I have no clue. But in my experience, even if it's inaccurate, the number is still useful for figuring out whether or not to ease up the overclocking or something.)

Well, it's an Intel e4400, so ya, it's pretty cheap (was only worth $120 over a year and a half ago).

---

### Post by CatKiller on 2009-10-02
It's not that difficult to tell the difference between 30° and 60°. Take the case off and have a feel.

---

### Post by ownaginatious on 2009-10-02
Heh, that won't exactly work since there is a large heat sync preventing me from actually physically touching the surface of the processor.

---

### Post by CatKiller on 2009-10-02
I wasn't suggesting that you touch the processor itself. The heatsink is going to be at a similar temperature to the processor, and should certainly be enough to tell you whether your processor is actually running 30° hotter in Ubuntu than Windows.

---

### Post by ownaginatious on 2009-10-02
> **CatKiller said:**
> I wasn't suggesting that you touch the processor itself. The heatsink is going to be at a similar temperature to the processor, and should certainly be enough to tell you whether your processor is actually running 30° hotter in Ubuntu than Windows.

Well, I have a large heat sync with many fins, so most of the heat is displaces by the time the heat reaches the extremities. This makes it difficult to judge the internal temperature from the exterior.

Anyway, I'm not really concerned about the system burning up; the issue is I would like to know the temperature, accurately.

---

### Post by Giblet5 on 2009-10-02
I have a Fluke DMM on my desk with its probe down in the tank of water that circulates over my CPU, GPU, and chipset.

It's accurate within +/-0.2C and takes up no screen real estate. I calibrated it two weeks ago and it was dead-on.

34.6C right now.

If you want to be nerdy, then at least try to clutter your desk with nerdly goods. That's what I always say, and my wife tells me "Stop saying that!"

---

### Post by Lord Stig on 2009-10-12
My friend has a E5200 processor which doesn't appear to be running too hot (although I am no expert). He tried Intrepid which installed successfully through windows (Wubi, I think it's called?) but it would restart either during boot up (the progress bar would move left to right, then right to left in the familiar powering down way) and other times it'd boot Ubuntu ok but he'd get a couple of minutes out of it before it shut down. No message was given as to why.
He's just tried Jaunty which has the same problems but does apparently report why this time - it says the CPU temperature is too hot and reports 25C. That doesn't sound that hot to me (but see first set of brackets, above). He's checked the BIOS which says the maximum running temperature cut off is 90C (too hot I would guess??).
He doesn't have any temperature-measuring Windows programs but he doesn't have this restarting problem in it. Puppy is also affected in the same way as Ubuntu.
Reading these forums and others I understand the problems in Linux interpreting the temperature data it gets. Is there a command line switch on bootup or something in the BIOS he can try?

---

