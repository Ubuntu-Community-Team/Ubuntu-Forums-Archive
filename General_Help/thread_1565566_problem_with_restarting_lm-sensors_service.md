---
title: "problem with restarting lm-sensors service"
date: 2010-09-01
forum: General Help
---

### Post by mahmoodn on 2010-09-01
I can not restart lm-sensos service. This is what I get:
```
mahmood@localhost:~$ sudo /etc/init.d/lm-sensors restart
.: 39: Can't open /etc/init.d/functions
```
Thanks for any idea.

---

### Post by NewDisciple on 2010-09-01
From the terminal just run: sensors. Do you get anything from that? Are you running an applet for your sensors? Are you manually starting it or do you have it set to run automatically at each startup?

---

### Post by mahmoodn on 2010-09-01
The output of sensors is normal:
```
mahmood@localhost:detect$ sudo sensors
it8720-isa-0290
Adapter: ISA adapter
in0:         +0.86 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.58 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.39 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in5:         +3.12 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.03 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:        +3.10 V
fan1:       1708 RPM  (min =   10 RPM)
fan2:        636 RPM  (min =    0 RPM)
fan3:       1283 RPM  (min =   10 RPM)
fan4:       1205 RPM  (min =    0 RPM)
temp1:       +35.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp2:       +25.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp3:       +35.0Â°C  (low  = +127.0Â°C, high = +90.0Â°C)  sensor = thermistor
cpu0_vid:   +0.313 V
```
Currently I am not using any applet. Also I want to manually restart lm-sensors daemon

---

### Post by NewDisciple on 2010-09-01
Have you tried /usr/bin/sensors? I'm not sure what your goal is by a manual start-up, since a daemon is a program running in the background. It seems to me that it would be best to have it start when you boot-up.

---

### Post by hangfire on 2010-09-01
> **mahmoodn said:**
> I can not restart lm-sensos service. This is what I get:
```
mahmood@localhost:~$ sudo /etc/init.d/lm-sensors restart
.: 39: Can't open /etc/init.d/functions
```
Thanks for any idea.

I suspect this is a local PATH issue. Try the sudo by first cd'ing to the /etc/init.d directory, then run the sudo command.

-HF

---

### Post by mahmoodn on 2010-09-02
> **NewDisciple said:**
> Have you tried /usr/bin/sensors? I'm not sure what your goal is by a manual start-up, since a daemon is a program running in the background. It seems to me that it would be best to have it start when you boot-up.

/usr/bin/sensors is fine. As I said "sudo sensors" show the sensors information. What I mean by "manual" is restarting the service without rebooting

> **hangfire said:**
> I suspect this is a local PATH issue. Try the sudo by first cd'ing to the /etc/init.d directory, then run the sudo command.

-HF
```
mahmood@localhost:init.d$ cd /etc/init.d/
mahmood@localhost:init.d$ sudo lm-sensors restart
sudo: lm-sensors: command not found
mahmood@localhost:init.d$ ls lm*
lm-sensors 
```
As you see lm-sensors is present but I don't know why it doesn't work!

---

### Post by llawwehttam on 2010-09-02
when in the sensors directory you can't use:

```
sudo lm-sensors restart
```you need to use:
```
sudo ./lm-sensors restart
``` IIRC

---

### Post by mahmoodn on 2010-09-02
```
mahmood@localhost:~$ cd /etc/init.d/

mahmood@localhost:init.d$ sudo ./lm_sensors restart
.: 39: Can't open /etc/init.d/functions

mahmood@localhost:init.d$ ls -l lm*
-rwxr-xr-x 1 root root 2969 2010-09-02 12:49 lm_sensors
```
It is starnge. Can someone please post the output of "sensors" for core-i7 (if there is any)?

Thanks,

---

