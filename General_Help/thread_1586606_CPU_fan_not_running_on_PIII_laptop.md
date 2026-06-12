---
title: "CPU fan not running on PIII laptop"
date: 2010-10-02
forum: General Help
---

### Post by dmizer on 2010-10-02
My CPU fan is not running on my PIII DELL laptop. I used to be able to force the fan to come on by echoing changes to /proc/acpi/thermal_zone/THRM/trip_points but this is apparently no longer possible as trip_points is read only and is set as follows:
```
# cat trip_points 
critical (S5):           120 C
passive:                 85 C: tc1=4 tc2=3 tsp=300 devices=CPU0 
active[0]:               65 C: devices=FAN0
```
Clearly, these are not ideal temperatures.

Also, there is no fan listed in /proc/acpi/fan/

Laptop is a DELL Latitude x200 model PP03S

Possibly relevant output
```
# cat cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Mobile Intel(R) Pentium(R) III CPU - M   933MHz
stepping	: 4
cpu MHz		: 399.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
bogomips	: 797.36
clflush size	: 32
cache_alignment	: 32
address sizes	: 36 bits physical, 32 bits virtual
power management:
```
```
# dmidecode | head -n10
# dmidecode 2.9
SMBIOS 2.3 present.
39 structures occupying 1183 bytes.
Table at 0x000D3010.

Handle 0x0000, DMI type 208, 10 bytes
OEM-specific Type
	Header and Data:
		D0 0A 00 00 01 04 FE 00 22 01
```

How do I keep my laptop from melting?

---

### Post by gzarkadas on 2010-10-02
Hi, not have a Dell, but I have found the following threads related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/160291](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/160291)
This is for a Dell Inspiron 9300 (but applies to other models too, read below).
_Suggests:_ Load the i8k.ko driver and use gkrellm to control the fans.
You may need to do (see post #10 there) a:
```

sudo echo i8k >> /etc/modules
sudo echo options i8k force=1 >> /etc/modprobe.d/i8k.modprobe

```Have a look also at post #17.

The thread links to [http://ubuntuforums.org/archive/index.php/t-472567.html](http://ubuntuforums.org/archive/index.php/t-472567.html) in which one it is suggested to install the  i8kutils package (contains utilities to monitor/control fans in Dells).

The "final" solution that reported to work there was:

> 
Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then  configure your fan thresholds in settings - plugins - Dell i8k
I have also found two threads below that are _*not*_ for Dells and the workaround is reported to *not* always work; but you may want to give them a try, if the solution above does not work:

[http://ubuntuforums.org/showthread.php?t=1317507&page=2](http://ubuntuforums.org/showthread.php?t=1317507&page=2)
Suggests: Add `acpi_osi=Linux' to kernel command line (by adding it to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
Suggests: Add `acpi.power_nocheck=1 acpi_osi=linux' to kernel command line

I hope these will help.

---

### Post by Laysan_A on 2011-01-24
I don't know if this really applies, but I thought I'd throw it out there anyway, just in case. Currently Gkrellm is compiled in Ubuntu without libsensors support. This doesn't seem to be a problem with my wife's e1705, and perhaps won't affect other dell models with intel processors, but just in case, I thought I'd bring it up. If you find you need libsensors support for your sensors, you'll have to compile gkrellm yourself from source (it's very straightforward). There's a bug report [here.](https://bugs.launchpad.net/ubuntu/+source/gkrellm/+bug/688944)

The other thing I wanted to mention concerns some dell models being unable to get support using i8kutils. I'm not absolutely certain about this, so you may want to do your own research, but I think it's reasonable to assume that the i8k module is derived from the bsd port of the original i8kfan dos utility, later to become i8kfanGUI, by Christian Deiter. His wepage contains a list of at least some supported dell models, as well as some that are not supported. [Here is his page](http://www.diefer.de/i8kfan/).

---

