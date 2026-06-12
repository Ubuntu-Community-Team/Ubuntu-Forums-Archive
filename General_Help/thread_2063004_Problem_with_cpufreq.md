---
title: "Problem with cpufreq"
date: 2012-09-26
forum: General Help
---

### Post by LordVahid on 2012-09-26
Hi, 
I am an Ubuntu user. I have a Core i7 2600 on ASUS P8Z77-Pro motherboard.
Everytime I try to assign different frequencies to cores, I get the wrong result.
I try to set Core 0 freq to 1.6 and Core 3 to 3.4, but when I run some SPEC benchmarks, I get the same result in execution time on two cores. 
I tried to use following commands:
echo 1600000 >/sys/devices/.../cpu0/scaling_setspeed
and 
echo 1600000 >/sys/devices/.../cpu0/scaling_max_frequency
and 
echo 1600000 >/sys/devices/.../cpu3/scaling_setspeed
echo 3401000 >/sys/devices/.../cpu3/scaling_max_frequency
but got the same results and when I tried to run the cpufreq-info, I got the following message:
Core 0:
current policy: frequency should be within 1.60 GHz and 1.60 GHz,
 the governor "userspace" ...
and current CPU frequency is 3.4 GHz (asserted by call to hardware) ? ? ? ? ?

---

### Post by Doug S on 2012-09-26
Hi and welcome to Ubuntu forums. 
 
For some specific testing I have been doing over many months now, I have had to lock the cpu frequencies. I have not experienced the troubles you described, although I have never used the "userspace" governor mode before. I tried it and it worked as expected. I also do not use the cpufrequtils, but rather do everything manually. Example script:```
doug@s15:~/temp$ cat set_cpu_userspace
#! /bin/bash
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
echo "userspace" > /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
echo 2100000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
echo 2200000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_setspeed
echo 2300000 > /sys/devices/system/cpu/cpu2/cpufreq/scaling_setspeed
echo 2400000 > /sys/devices/system/cpu/cpu3/cpufreq/scaling_setspeed
echo 2500000 > /sys/devices/system/cpu/cpu4/cpufreq/scaling_setspeed
echo 2600000 > /sys/devices/system/cpu/cpu5/cpufreq/scaling_setspeed
echo 2700000 > /sys/devices/system/cpu/cpu6/cpufreq/scaling_setspeed
echo 2800000 > /sys/devices/system/cpu/cpu7/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
grep MHz /proc/cpuinfo
doug@s15:~/temp$

```And example output from the script:```
doug@s15:~/temp$ sudo ./set_cpu_userspace
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
userspace
userspace
userspace
userspace
userspace
userspace
userspace
userspace
cpu MHz         : 2100.000
cpu MHz         : 2200.000
cpu MHz         : 2300.000
cpu MHz         : 2400.000
cpu MHz         : 2500.000
cpu MHz         : 2600.000
cpu MHz         : 2700.000
cpu MHz         : 2800.000
doug@s15:~/temp$

```By the way (for other readers), the list of frequencies I could use was found via:```
doug@s15:~/temp$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
[sudo] password for doug:
3401000 3400000 3300000 3200000 3100000 3000000 2900000 2800000 2700000 2600000 2500000 2400000 2300000 2200000 2100000 1600000
doug@s15:~/temp$

```

---

### Post by LordVahid on 2012-09-27
Hi, Thank you for your answer. I did it as you said in your answer, but consider the following:
when I run the gcc benchmark in 3.4 GHz freq., I get the answer in 320s. 
when I run it in 1.6 GHz of freq., I get the answer in like 509s.
when I config my cpu frequencies as you said, and run my benchmarks on two Cores of my processor, I get the same result in time, and when it is running the benchmarks, I get the same frequencies from cpufreq-info as I said in my post.
there is a paradox in the results of 
cpufreq-info,
and 
cat /sys/.../scaling_cur_freq
the first one shows which I said in my first post, and the second command return right results of frequencies.
Thanks

---

### Post by Doug S on 2012-09-27
O.K., I get the same as you, and I agree it doesn't make sense, based on my understanding of how it should work.
 
I have my own CPU loading program. I used "taskset" to force it to run on cpu 0 on one ssh session and on cpu 7 on another. Supposedly cpu 0 was at 1600 MHz and cpu 7 was at 3400 Mhz, and all cpus were in "userspace" mode. I used "top", on a 3rd ssh session, to confirm that indeed cpus 0 and 7 were at 100%. I still do not have those cpufreq utilites, but I used "grep MHz /proc/cpuinfo" to supposedly confirm cpu clock rates were as expected. The loop rates were the same on the two whereas the expectation was that they would differ by a factor of over 2. Interesting...
 
Edit: The only way I could really get the lower clock rates was to have all 8 cpus in "powersave" mode. Then the loop rate was the expected over 2 times lower.

---

### Post by LordVahid on 2012-09-27
Thanks by the way, but I think it differs from what Intel says. They say that these CPU`s have the local DVFS capability. But the results say something else.

---

### Post by Doug S on 2012-09-27
I am convinced this stuff used to work as we think it should.
 
I went back to kernel 3.2.0-27 and, so far with limiting testing, things are working as expected. I am seeing over 2 times slower performance on cpu 0 compared to cpu 7, as expected with how I have the clock frequencies set. Therefore I am concluding that this is some very recently introduced bug.
 
I am out of time for now, but will come back to this later. I still have another couple of kernels between -27 and the current -31 (I think it is). I try to isolate it better and test more completley, perhaps tonight.
 
Edit: Unable to repeat test results mentioned above with older kernel. Note only "powersave" and "performance" modes were used for those tests. Unable to make any sense at all out of "userspace" mode, even with all cpu's set to the same frequency all cpu's seem to jump to max clock freqeuncy.

---

### Post by Doug S on 2012-09-28
I found this in some documentation:```
cpuinfo_cur_freq: Current frequency of the CPU as obtained from the hardware, in KHz. This is the frequency the CPU actually runs at.
```which I think is what is actually behind this (from post #1 above):```
and current CPU frequency is 3.4 GHz (asserted by call to hardware) ? ? ? ? ?
```. However I have a situation where that value is wrong, saying 3401000 instead of the actual 1600000, based on loop execution times.
 
Details: I used this script:```
doug@s15:~/temp$ cat set_cpu_inquire_freqs
#! /bin/bash
echo " "
echo "Current CPU frequency governors:"
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
echo " "
echo "CPU frequencies via a what the kernel thinks they are (/proc/cpuinfo) method:"
grep MHz /proc/cpuinfo
echo " "
echo "CPU frequencies via the what they actually are (hardware read) method:"
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu4/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu5/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu6/cpufreq/cpuinfo_cur_freq
cat /sys/devices/system/cpu/cpu7/cpufreq/cpuinfo_cur_freq
echo " "
echo "CPU frequencies via another what the kernel thinks they are (scaling_cur_freq) method:"
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_cur_freq
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_cur_freq
echo " "
echo "CPU set frequencies, only applicable when using the userspace governor:"
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_setspeed
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_setspeed
echo " "
doug@s15:~/temp$

```and ran a CPU loading program on cpu 0 and 2 where the loop rate results indicated 1.6 GHz clock rate. But with this results from the script:```
doug@s15:~/temp$ sudo ./set_cpu_inquire_freqs
Current CPU frequency governors:
powersave
performance
powersave
performance
powersave
performance
powersave
performance
CPU frequencies via a what the kernel thinks they are (/proc/cpuinfo) method:
cpu MHz         : 1600.000
cpu MHz         : 3401.000
cpu MHz         : 1600.000
cpu MHz         : 3401.000
cpu MHz         : 1600.000
cpu MHz         : 3401.000
cpu MHz         : 1600.000
cpu MHz         : 3401.000
CPU frequencies via the what they actually are (hardware read) method:
3401000
3401000
3401000
3401000
3401000
3401000
3401000
3401000
CPU frequencies via another what the kernel thinks they are (scaling_cur_freq) method:
1600000
3401000
1600000
3401000
1600000
3401000
1600000
3401000
CPU set frequencies, only applicable when using the userspace governor:
<unsupported>
<unsupported>
<unsupported>
<unsupported>
<unsupported>
<unsupported>
<unsupported>
<unsupported>
doug@s15:~/temp$

```

---

### Post by LordVahid on 2012-10-09
bility in this processors yet?

---

### Post by LordVahid on 2012-10-09
I spoke with one of Intel`s support agents and told her my problem. They assert the Intel i7 2600 has the local DVFS tech. which is the ability to change cores` frequencies independent of other cores` frequencies. If it is so, then why we are not able to do that?
Is this a kernel bug?! Or there is not this capability in this processors yet?

---

### Post by LordVahid on 2012-10-09
I spoke with one of Intel`s support agents and told her my problem. They assert the Intel i7 2600 has the local DVFS tech. which is the ability to change cores` frequencies independent of other cores` frequencies. If it is so, then why we are not able to do that?
Is this a kernel bug?! Or there is not this capability in this processors yet?

---

### Post by Doug S on 2012-10-09
I don't know the answers to your questions.
I did find using the turbostat program very useful to really know the various CPU frequencies, as the "actual" frequencies via```
cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
```seems to often be incorrect.
Note 1: I compiled turbostat myself, as it is included in the kernel source, however I believe it is also available via the linux-tools-common package.
Note 2: turbostat requires the module msr to be loaded (but it will tell you that when you try to run it).
 
My testing results remain inconsistent, but I have been unable to get two cores to run at different frequencies.

---

### Post by pqwoerituytrueiwoq on 2012-10-09
> **LordVahid said:**
> I spoke with one of Intel`s support agents and told her my problem. They assert the Intel i7 2600 has the local DVFS tech. which is the ability to change cores` frequencies independent of other cores` frequencies. If it is so, then why we are not able to do that?
Is this a kernel bug?! Or there is not this capability in this processors yet?
I have never had issues with my CPUs (all happen to be AMD) changing speeds independently with the exception of my Pentium 4 and Pentium 3 CPUs single core chips

the speed is probably changing automatically and you are not seeing it
run this command to see what speed your cpu cores are running at

most of us like to use the same policy for setting core speeds on the CPU (eg ondemand/conservative)
```
sudo cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
```
i have never seen turbo working (only system i have that supports it is my dads)

---

### Post by Doug S on 2012-10-09
@ pq....q:> i have never seen turbo working (only system i have that supports it is my dads)Actually, "/sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq" doesn't report if the CPU is running at turbo frequencies, whereas turbostat does.
I have plenty of evidience (for my system, at least) that:```
/sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
``` often gives incorrect information.
 
Edit:
@LordVahid: Here is an interesting, and brief, [whitepaper]("http://download.intel.com/design/processor/applnots/320354.pdf") . Here is an excerpt:> All active cores in the processor will operate at
the same frequency. Even at frequencies above
the base operating frequency, all active cores will
run at the same frequency and voltage...

---

### Post by maudebian on 2012-10-11
Hi all

this seems quite interesting to me, since I'm experiencing similar issues since 3.6 kernel. Oddly enough, I could only find this thread about a similar issue after 3 days of intense googling... is anyone running a recent kernel out there...?!?

On my laptop (a Clevo W150HRM with an i7 2720QM CPU) I'm currently using Debian wheezy/sid with the aptosid 3.6-1.slh.3 kernel: since the first 3.6 kernel I noticed the idle temperatures increased by ~10°C, therefore I decided to dig into that.

In my case it seems that, while the ondemand governor "believes" it has successfully changed the CPU frequency (sysfs [FONT=Courier New]scaling_cur_freq[/FONT] varies as usual depending on system load), the frequency remains stuck at or over (turbo boost) the max according to [FONT=Courier New]cpuinfo_cur_freq[/FONT], [FONT=Courier New]turbostat[/FONT] and [FONT=Courier New]cpufreq-info[/FONT], just like the performance governor has been set.

It seems no [FONT=Courier New]cpufreq-set[/FONT] setting can lower the idle frequency in any way, even by changing governor; but as soon as I reboot to a 3.5.5 kernel the idle temps decrease back by 10°C and [FONT=Courier New]cpuinfo_cur_freq[/FONT] begin to follow [FONT=Courier New]scaling_cur_freq[/FONT] just as expected.

Regarding turbo boost, turbo frequencies have always been reported as max+1000kHz in sysfs files, only [FONT=Courier New]i7z[/FONT] and [FONT=Courier New]turbostat[/FONT] can offer more details on that AFAICS.


Mau


edit: forgot to mention that my AMD Phenom box, using the powernow-k8 cpufreq driver, doesn't show this issue

---

### Post by Doug S on 2012-10-12
I loaded Kernel 3.6.1. The pre-built one from the [Ubuntu Kernel-ppa ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")area, not the build it myself from kernel.org version. I am not observing the issues noted by maudebian. While my testing has been minimal, so far the results are the same as previously.

---

### Post by maudebian on 2012-10-12
Tried to compile a vanilla 3.6.1 kernel: same behavior. I opened a [bug on bugzilla.kernel.org]("https://bugzilla.kernel.org/show_bug.cgi?id=48721"), let's see what comes out.

---

### Post by OneOfMany07 on 2012-10-24
Glad I'm not the only one having trouble with forcing a CPU frequency!

And interesting the behavior might be different with an older kernel, or not using "userspace".  I know "performance" forces you to run at max frequency, but I didn't know until a Google ago that "powersave" runs at min.

It still seems like this is broken, but at least it gives me ideas to work around my issue too.

---

