---
title: "LM-sensors help"
date: 2010-03-24
forum: General Help
---

### Post by yeleek on 2010-03-24
Hi,

The LM-Sensors package with 9.10 doesn't support my hardware (i5 cpu) so have compiled and installed lm-sensors 3.1.2.

when running sensors-detect it says to add the below to  /etc/rc.d/rc.local

# Chip drivers
modprobe it87
/usr/local/bin/sensors -s

 /etc/rc.d/rc.local doesn't exist so have added it to /etc/rc.local - trust this is ok?

On reboot running sensors produces this

it8720-isa-0290
Adapter: ISA adapter
in0:         +0.88 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.60 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.42 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.37 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.15 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.03 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.14 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +3.09 V
fan1:       1591 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
temp1:       +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +22.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.313 V


Is that right?  Thought it would list the 4 cores of my i5?

Thanks

---

### Post by yeleek on 2010-03-25
bump

---

### Post by Mark Phelps on 2010-03-25
I did the same thing (compiled new LM-Sensors) for my dual-core CPU and I only get one CPU temp reading -- not a temp for each core.

And, I have the same thermal sensor chip (it87).

Sorry, can't provide any addition help.

---

### Post by Irony on 2010-03-25
I have an Intel Core i5 750 chip and I get nothing with the sensor command;

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

In Windows 7 I have no problem...

---

### Post by yeleek on 2010-03-25
> **Mark Phelps said:**
> I did the same thing (compiled new LM-Sensors) for my dual-core CPU and I only get one CPU temp reading -- not a temp for each core.

And, I have the same thermal sensor chip (it87).

Sorry, can't provide any addition help.

OK thanks :)

---

### Post by yeleek on 2010-03-25
> **Irony said:**
> I have an Intel Core i5 750 chip and I get nothing with the sensor command;

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

In Windows 7 I have no problem...

Are you using LM-Sensors from the repositories or compiled your own?  The one in the repositories cannot see the thermal sensor.

---

### Post by DeMus on 2010-03-25
I still believe it is a fault in the kernel. Version 2.6.30 was okay, all newer versions have problems. At the moment I use 2.6.33 and my sensors don't function as they used to.

---

### Post by Irony on 2010-03-25
> **yeleek said:**
> Are you using LM-Sensors from the repositories or compiled your own?  The one in the repositories cannot see the thermal sensor.

Repository 64 bit Karmic.

It looks like sensors doesn't work on 2.6.31 kernel (apparently enabling it may damage your system);

[http://www.overclock.net/linux-unix/507585-how-linux-temps-system-monitors.html#post6228116](http://www.overclock.net/linux-unix/507585-how-linux-temps-system-monitors.html#post6228116)
[https://bugzilla.kernel.org/show_bug.cgi?id=13967](https://bugzilla.kernel.org/show_bug.cgi?id=13967)
[http://hansdegoede.livejournal.com/7932.html](http://hansdegoede.livejournal.com/7932.html)

---

