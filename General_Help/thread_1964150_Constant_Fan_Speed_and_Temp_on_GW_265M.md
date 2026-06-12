---
title: "Constant Fan Speed and Temp on GW 265M"
date: 2012-04-23
forum: General Help
---

### Post by jmooney776 on 2012-04-23
Hi All,

I hope this is the right forum for this...

I've got 10.04LTS on a Gateway 265M Laptop and the fan runs but the processor temps creep up to 60C with no activity and the fan runs constantly at a low speed.  I've done a lot of googling and forum searching and I've tried the suggestions in he recommended threads but I've hit a wall that none of them address.  I've used sensors-detect and install the module it suggested.

```
jim@jim-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +58.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +59.0°C  (high = +100.0°C, crit = +100.0°C)  


``` 

Then I do pwmconfig and get this:

```
jim@jim-laptop:~$ sudo pwmconfig
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

I seem to be left at a point where I can't configure the fan thresholds and get it to run cooler.  It's uncomfortable using it because the handrests get hot.

Any suggestions as to what my options are at this point?

Thanks,

Jim

---

