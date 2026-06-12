---
title: "System Clock Runs Slow"
date: 2010-01-04
forum: General Help
---

### Post by smerral on 2010-01-04
No matter what I try the system clock runs slow on Ubuntu. I have tried resetting, synchronizing with servers etc. all to no avail. I dual boot with XP pro. Before I installed Ubuntu the windows XP system clock ran fine. I have also noticed that the hardware clock is also affected - I have to reset that too sometimes. Again,I had no problems before I installed Ubuntu.

Any ideas?

Thanks in advance.

---

### Post by mgmiller on 2010-01-04
Many motherboards have a Lion battery that remembers BIOS settings and keeps the clock going when the machine is powered off.  If the battery is more than 3-4 years old, it may be winding down.  It's easy to have it checked at any Radio Shack or similar store.  Replacements are also available at Radio Shack for a few US$.  I find it hard to believe that Ubuntu did something to the hardware clock.  Since you are having the problem in both OS's, I suspect a hardware issue, in this case, a failing battery.  This type of battery keeps its voltage output fairly constant until it starts to fail, then it rapidly goes downhill.

---

### Post by smerral on 2010-01-04
Thanks for the reply. 

My laptop is only 18 months old or so. It is strange - I have set the hardware clock in BIOS and am now running Ubuntu. The system clock is beginning to run slow. If I run sudo hwclock I can see that this is so and the hardware clock is keeping time. So despite what may be wrong with the hardware clock there is clearly a problem with the system clock. If it were not for this and the fact that it was OK until I installed Ubuntu I would accept your battery diagnosis. 

Why the hardware clock is sometimes off I haven't worked out yet - it could be because I have tried various commands to get the system and hardware clocks to synchronise in Ubuntu. Once the hardware clock is set correctly in windows the system clock in windows is also fine.

Ah well, it is a minor problem for me - just bugs me a bit though.

---

### Post by jamesisin on 2010-01-04
Well, the bios battery should only be an issue when the machine is not either running or plugged into the wall outlet.

Are you seeing any other processor slowness problems?

Are you saying that the system clock in Ubuntu, the system clock in Windows, and the hardware clock are all being effected (though perhaps at differing rates)?

---

### Post by happyhamster on 2010-01-04
- Could you perhaps take a look in your log?  In a terminal (Applications --> Accessories-->Terminal), type (or copy & paste):

dmesg | grep clock -i

- It should show which clocksource is being used.

[edit: and which version of Ubuntu are you using?]

---

### Post by smerral on 2010-01-04
I'm using Ubuntu 9.10 and no, there are no other processor problems the system runs fine.
This is what I got when I enter dmesg | grep clock -i:

[    0.894660] rtc_cmos 00:04: setting system clock to 2010-01-04 18:05:31 UTC (1262628331)

---

### Post by smerral on 2010-01-04
well I found my clocksource by doing: 

cat/sys/devices/system/clocksource/clocksource0/current_clocksource

It is acpi_pm

Is there an alternative?

---

### Post by happyhamster on 2010-01-04
Weird, it doesn't show a clocksource (perhaps it's defaulting to "jiffies"?). Anyway, what kind of machine are you using? (Which processor?). And are you using 32 bits or 64bits Ubuntu?

You can check with the commands:

cat /proc/cpuinfo

uname -a

---

### Post by happyhamster on 2010-01-04
> **smerral said:**
> well I found my clocksource by doing: 

cat/sys/devices/system/clocksource/clocksource0/current_clocksource

It is acpi_pm

Is there an alternative?

That depends on your system. Modern systems usually use hpet or tsc.

---

### Post by smerral on 2010-01-04
Here's the info:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 22
model name	: Intel(R) Celeron(R) CPU          540  @ 1.86GHz
stepping	: 1
cpu MHz		: 1862.289
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3724.57
clflush size	: 64
power management:

Linux brian-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

---

### Post by smerral on 2010-01-04
apparently my alternative is tsc

---

### Post by happyhamster on 2010-01-04
> **smerral said:**
> apparently my alternative is tsc
- Did you find that using (found that one myself just a moment ago):
 
cat /sys/devices/system/clocksource/clocksource0/available_clocksource

- Anyway, what you can try is setting the clocksource as a boot-parameter: boot into the grub menu, highlight the kernel you want to boot and press "e". Then search for a line (it will be spread out over multiple lines):

linux /boot/vmlinuz......................................quiet splash

- And add:

clocksource=tsc

- Then press Ctrl-x to boot. Next, check if tsc is actually used, and, if so, if the clock behaves any better.

Note: this is a pretty safe procedure, because all will be back to normal after a reboot. Only when you're *sure* everything works fine, should you consider making that change permanent by editing grub.

Good luck, and keep us informed.

---

### Post by smerral on 2010-01-04
Yes I found the clocksource the way you said - I've been checking some other posts on the subject. Thanks for the advice - I will try it and see what happens!

---

### Post by tmorphius on 2010-01-04
you need to change the little button-sized battery on ur motherboard maybe?

---

### Post by smerral on 2010-01-04
Hey happyhamster I think you solved it! I've been running tsc for 45 minutes now and the time is perfectly matched with the hardware clock. I'll see what happens tomorrow before editing grub. BTW how exactly do you DO that? I have grub 2 so I know it isn't as simple as editing the menu.lst file.

Thanks a lot for the help.

---

### Post by happyhamster on 2010-01-04
> **smerral said:**
> Hey happyhamster I think you solved it! I've been running tsc for 45 minutes now and the time is perfectly matched with the hardware clock. I'll see what happens tomorrow before editing grub.
This is a laptop right? If so, keep an eye on the powermanagement stuff as well (battery life, cpu-frequency scaling, temperatures, etc.). acpi_pm is related to powermanagement, so perhaps using another clocksource can have unwanted side-effects.

> 
 BTW how exactly do you DO that? I have grub 2 so I know it isn't as simple as editing the menu.lst file.
- It's a similar procedure, but with the file /etc/default/grub instead. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

gksudo gedit /etc/default/grub

- Then find the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

- and change into:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=tsc" 

- Save, and update grub:

sudo update-grub

- Reboot and test.

> 
Thanks a lot for the help.
You're welcome, and let us know how things worked out :)

---

### Post by smerral on 2010-01-05
The clock problem appears to be solved, but in the process of monitoring my CPU I have found that it runs at 68 degrees which seems a bit a high. This has nothing to do with tsc as it is the same with acpi. Neither is it specific to Ubuntu as it is the same when I run XP - maybe it's always been like that as I have never checked it before.

Also when I try to run cpu scaling I get a message saying my hardware is misconfigured or does not support it.

---

### Post by happyhamster on 2010-01-05
> **smerral said:**
> The clock problem appears to be solved, but in the process of monitoring my CPU I have found that it runs at 68 degrees which seems a bit a high. This has nothing to do with tsc as it is the same with acpi. Neither is it specific to Ubuntu as it is the same when I run XP - maybe it's always been like that as I have never checked it before.
It's hot, but safe, according to this sheet from Intel:
[http://processorfinder.intel.com/Details.aspx?sSpec=SLA2F](http://processorfinder.intel.com/Details.aspx?sSpec=SLA2F)
(TPD = 27-32 W, Thermal specification = 100 degrees).

> 
Also when I try to run cpu scaling I get a message saying my hardware is misconfigured or does not support it.
There also wasn't any output about powermanagement when you ran cat /proc/cpuinfo, so perhaps it just isn't supported.

---

### Post by smerral on 2010-01-05
Once again thanks for the info and your help in fixing the clock problem - it's been bugging me for a few weeks. Any ideas why acpi would run slow in the first place?

---

### Post by happyhamster on 2010-01-05
It appears it's because of the hardware itself or the BIOS. It's pretty funny if you take a look at the source code for acpi_pm:

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/clocksource/acpi_pm.c](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/clocksource/acpi_pm.c)
Most of that code is hardware bug testing.

Basically what happens is that during boot, acpi_pm performs a series of tests to see if the hardware PowerManagement clock is reliable. If it's not, acpi_pm should exit, so an alternative clocksource can be used. But unfortunately, the check sometimes fails (for example because of the limited time available to perform those checks).
> 
197         for (j = 0; j < ACPI_PM_MONOTONICITY_CHECKS; j++) {


In other words: sometimes the PowerManagement clock is crap, and the kernel will detect this and do the right thing, but sometimes the clock just isn't crappy enough, and it slips under the radar.


[edit: another quote from the code:]
> 
231 /*
232  * Allow an override of the IOPort. Stupid BIOSes do not tell us about
233  * the PMTimer, but we might know where it is.
234  */

Funny stuff :)

---

### Post by smerral on 2010-01-06
ha ha yes weird :P guess that explains it

---

