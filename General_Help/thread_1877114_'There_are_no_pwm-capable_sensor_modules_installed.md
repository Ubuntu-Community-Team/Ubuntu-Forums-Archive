---
title: "'There are no pwm-capable sensor modules installed'"
date: 2011-11-07
forum: General Help
---

### Post by karol4722 on 2011-11-07
After reinstall my ubuntu 11.10 I can't control my fan speed (before reinstall everything was good)

Look at this:
```
root@muhahaha:/home/karol# sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +25.8°C  (high = +70.0°C)

```

```
root@muhahaha:/home/karol# pwmconfig
# pwmconfig revision 5857 (2010-08-22)
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
Before reinstall I had more sensors. What should I do? Ubuntu 11.10 64bit

---

### Post by overtone on 2011-12-03
Im having the same problem buddy. 


I'm following this tutorial for fan control. No luck with pwm though.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29)

---

### Post by shmatic on 2012-01-18
[FONT=Trebuchet MS][SIZE=2]Hi guys,

came across this and thought I'd share it.

If you are using a PWM capable motherboard with the IT87 module and 
you want to use fancontrol ...

[/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2]If you can't load the it87 module - most likely your kernel needs 
[/SIZE][/FONT][INDENT][FONT=Arial]'acpi_enforce_resources=lax' [/FONT]
  [/INDENT][FONT=Arial][FONT=Trebuchet MS]as kernel argument. Add it to your boot loader for example.
Then try 
  [/FONT][/FONT][INDENT][FONT=Arial]modprobe it87
lsmod | grep it87                     --> make sure it's loaded
[FONT=Trebuchet MS]sensors-detect 
    [/FONT][/FONT][/INDENT][FONT=Arial][FONT=Trebuchet MS]save configuration, then run
[/FONT][/FONT][INDENT][FONT=Arial][FONT=Trebuchet MS]sensors[/FONT][/FONT][FONT=Trebuchet MS]
[/FONT][/INDENT][FONT=Trebuchet MS][SIZE=2]to make sure everything loads properly. [/SIZE][/FONT]
[FONT=Arial][FONT=Trebuchet MS]
Then try 
[/FONT][/FONT][INDENT][SIZE=1][FONT=Arial][FONT=Trebuchet MS]pwmconfig[/FONT][/FONT][/SIZE]
[/INDENT][FONT=Trebuchet MS] if  [/FONT][FONT=Trebuchet MS][SIZE=2]pwmconfig gives you:

[B]There are no pwm-capable sensor modules installed
[/B]
You can get it working by loading the it87 module with the command:

[/SIZE][/FONT][INDENT][FONT=Trebuchet MS][SIZE=2]modprobe it87 fix_pwm_polarity=1[/SIZE][/FONT]
[/INDENT][FONT=Trebuchet MS][SIZE=2]
pwmconfig should work as expected.

[/SIZE][/FONT]

---

