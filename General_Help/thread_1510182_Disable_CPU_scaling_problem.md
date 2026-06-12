---
title: "Disable CPU scaling problem"
date: 2010-06-15
forum: General Help
---

### Post by ibob_gr on 2010-06-15
Hello

I want to be able to disable CPU scaling, whenever I want. The reason is that I run some timing tests, and I want the results to be reproducable (ie the CPU running at the same frequency).

I have tried the following on 9.10 and 10.04 (both amd64).

I use rcconfig to disable "on demand" (from [http://ubuntuforums.org/showthread.php?t=1209386](http://ubuntuforums.org/showthread.php?t=1209386)) but then when I use cpufreq-info tool I get:

```

$ cpufreq-info 
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.10 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.10 GHz:98.33%, 2.10 GHz:0.01%, 1.60 GHz:0.00%, 1.20 GHz:0.00%, 800 MHz:1.66%  (134)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.10 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.10 GHz:98.33%, 2.10 GHz:0.00%, 1.60 GHz:0.00%, 1.20 GHz:0.00%, 800 MHz:1.66%  (105)

```

So, how do I disable the CPU scaling?

---

### Post by philinux on 2010-06-15
Add the cpu frequency scaling applet to a panel

Right click > Add to Panel.

---

### Post by ibob_gr on 2010-06-15
You are right, after using the applet, cpufreq-info reports the usage of governor "userspace" .

To change this from command line, the only solution is to write to /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor ? I try to but I can't

```
sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```

even if it's
```
$ ls -al /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
-rw-r--r-- 1 root root 4096 2010-06-15 14:28 /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

---

### Post by philinux on 2010-06-15
Left click the panel applet.

---

### Post by ibob_gr on 2010-06-15
Post #3 was not about using the applet. I had used the applet, and I mentioned that the applet *does* change the scaling governor.

I was then trying to use command line, to do the same thing, but I couldn't.

My question is how to change the scaling governor by command line. If you need a better description or any more output for the command line solution, I can post it.

---

### Post by philinux on 2010-06-15
> **ibob_gr said:**
> Post #3 was not about using the applet. I had used the applet, and I mentioned that the applet *does* change the scaling governor.

I was then trying to use command line, to do the same thing, but I couldn't.

My question is how to change the scaling governor by command line. If you need a better description or any more output for the command line solution, I can post it.

Ah you need 

```
sudo -i
``` first, then your command. Then type logout.

---

### Post by ibob_gr on 2010-06-15
Yep, that does it. Thanks for both answers!

Now if you have an explanation or a reference, as to why the shell is needed, I wouldn't mind reading :)

---

### Post by philinux on 2010-06-15
> **ibob_gr said:**
> Yep, that does it. Thanks for both answers!

Now if you have an explanation or a reference, as to why the shell is needed, I wouldn't mind reading :)

I've been looking. Sudo should be enough but some file permissions are different to others. 

-i is the preferred way.
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by philinux on 2010-06-15
> **ibob_gr said:**
> Yep, that does it. Thanks for both answers!

Now if you have an explanation or a reference, as to why the shell is needed, I wouldn't mind reading :)

From [jpeddicord]("http://ubuntuforums.org/member.php?u=90021")
> It's because the > operator is handled by non-root bash, and not by the echo command. Bash will run "echo ondemand" as root, then try to take the output of that and place it in /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor.

So, bash must be run as root, otherwise it cannot write to the file. An alternative, more sudo-ish way to go about it is to use:
Code:

```
sudo bash -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
```

This tells bash (which is now running as root) to run the command in quotes and then exit. This applies to other shells as well.

---

### Post by ibob_gr on 2010-06-18
Thanks for both answers :)

---

### Post by FactTech on 2010-06-22
This isn't exactly the same problem, but I'm hoping that phililinux might have some advice on it...

I have a fresh install of 10.04 (Lucid) on a laptop with a 2.0GHz P4 CPU. When I tried to install the GNOME CPU frequency scaling app, it wouldn't let me, saying frequency scaling is unsupported. After doing some reading, I added p4_clockmod to /etc/modules, and, after a reboot, I was able to install the applet without trouble.

However, now I am finding that the applet is only able to report the CPU state, not change it. It remains stuck on "Performance" mode no matter what I do... even the command line suggestions above result in no change.

Any suggestions?

---

### Post by guy-rouillier on 2010-06-27
I have a P4 630 3 GHz.  You may be in the same boat I am.  Run this:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver

and see what you get.  I get "acpi-cpufreq", even though, like you I have p4-clockmod in /etc/modules.  I found a post somewhere (sorry, been doing a lot of reading trying to solve this) that said because acpi-cpufreq is compiled into the kernel and p4-clockmod is a module, the former gets loaded and assigned by cpufreq before p4-clockmod ever gets a chance.

According to the authors, the only way to solve this is to recompile the kernel and remove all the drivers from the kernel, making them all modules.  Then you can assign the one you want.

If anyone finds an alternate solution that works, I'd like to hear about it.  I used Ubuntu for a file server specifically because I didn't want to be recompiling the kernel.  I use Gentoo for my desktop and get enough compiling there.

Thanks.

---

