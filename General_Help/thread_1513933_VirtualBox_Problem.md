---
title: "VirtualBox Problem"
date: 2010-06-20
forum: General Help
---

### Post by colinireland on 2010-06-20
Hello Everyone,

I have just installed Virtualbox 3.2.4 on Lucid. I have run into a problem. Everything seems to work fine until I virtualbox starts to create a new hard drive. It just hangs at 0% and never moves even after leaving it for 2-3 hours. The same thing happens for versions 3.1.8 and the OSE version in the repositories. Has anyone had the same problem? Does anyone know what might be going on? 

Any help would be greatly appreciated.

Regards,
Colin

Heres the dmesg output if its any use:

[   24.592237] eth1: no IPv6 routers present
[  101.277955] padlock: VIA PadLock not detected.
[  194.384318] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2056.520923] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 2056.520927] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[ 2056.520928] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[ 2056.520930] vboxdrv: the usage of hardware performance counters by
[ 2056.520931] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[ 2056.520934] vboxdrv: Found 2 processor cores.
[ 2056.521023] vboxdrv: fAsync=0 offMin=0x190 offMax=0x1c16
[ 2056.521070] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 2056.521072] vboxdrv: Successfully loaded version 3.1.8 (interface 0x00100001).
[ 2183.794259] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
user@compaq:~$

---

### Post by t1nm@n on 2010-06-20
hey, what is your harddrive partition size... imeant your ubuntu "/" . i think your problem is that you are trying for more space ...than that in your partition... if that is not the case..please post again

---

### Post by colinireland on 2010-06-20
Hey,

Never even thought of that. My / partition is 30Gb. I have 25Gb free. I thought the harddrive was created in the .VirtualBox folder in my home folder though.

---

### Post by colinireland on 2010-06-20
Prob should have said in my last post that I was trying for a 15Gb virtual drive. Also since my /home partition is encrypted, would this cause any problems?  I'd doubt it but just thought I'd mention it.

---

