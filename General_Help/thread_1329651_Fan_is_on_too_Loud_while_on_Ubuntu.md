---
title: "Fan is on too Loud while on Ubuntu"
date: 2009-11-17
forum: General Help
---

### Post by xxhopingtearsxx on 2009-11-17
Since I've switched to Ubuntu, I've noticed something.. my fan is on louder when I'm on Ubuntu. I have as much Windows as I do when I'm on Vista. Not much memory is used.. I'm using even less. The air that's coming out of my fan isn't really hot.. so it seems something is wrong. I'm sort of a newbie, but I can follow instructions well.. as long as it doesn't lead to the destruction of my tacky-plastic $299 Toshiba L305-S5955 laptop. I have 2GB of RAM btw.

---

### Post by CrusaderAD on 2009-11-17
You're specs really dont have much to do with your fan. Does your fan get loud when booting to other operating systems? I've never heard of a fan being effected by the operating system but I could be wrong.

---

### Post by xxhopingtearsxx on 2009-11-18
This is the first time it's happened.. maybe something changed with Ubuntu 9.10.. Idk. But it's bothering me. :[ Is there a settings somewhere that will allow me to change the fan speed?

---

### Post by CrusaderAD on 2009-11-18
Not in the operating system I don't think... possibly in your bios settings when you first boot up.

---

### Post by openuniverse on 2009-11-18
.

---

### Post by CrusaderAD on 2009-11-18
> **openuniverse said:**
> i get a loud fan when i first boot up, whether it's winxp or ubuntu 9.10. then it stops a minute or so later. that makes sense to me, because when both operating systems are booting they're doing a lot of stuff on this old cpu. more procs, faster louder fan, less procs (or you know, less busy ones) slower, quieter fan.

if it continues it's because some process is using a ton of cpu. nothing that system monitor shouldn't be able to point out, or top or htop for that matter. but if it's all the time, that *is *weird.

Makes sense.

---

### Post by ibuclaw on 2009-11-18
> **xxhopingtearsxx said:**
> This is the first time it's happened.. maybe something changed with Ubuntu 9.10.. Idk. But it's bothering me. :[ Is there a settings somewhere that will allow me to change the fan speed?

Fan devices are generally left up to the Motherboard's SBIOS to alter as it sees fit via the DSDT - which contains all ACPI information for your system (in the case of a fan, it's mostly to do with temperature detection and what throttle/burst speeds to go into when at a certain temperature).

If the fan is present/implemented in your Motherboard's DSDT, then Linux will show it under /proc/acpi/fan.
Run:
```
ls /proc/acpi/*
```
And post the output in your next post.

Regards
Iain

---

### Post by xxhopingtearsxx on 2009-11-18
```
joey@ubuntu:~$ ls /proc/acpi/*
/proc/acpi/dsdt   /proc/acpi/fadt  /proc/acpi/sleep
/proc/acpi/event  /proc/acpi/info  /proc/acpi/wakeup

/proc/acpi/ac_adapter:
ADP0

/proc/acpi/battery:
BAT0

/proc/acpi/button:
lid  power

/proc/acpi/embedded_controller:
EC0

/proc/acpi/fan:
FAN

/proc/acpi/power_resource:
FN00

/proc/acpi/processor:
CPU0

/proc/acpi/thermal_zone:
THRM

/proc/acpi/video:
OVGA
joey@ubuntu:~$ 

```

---

### Post by Sin@Sin-Sacrifice on 2009-11-18
I'd say go with the advice on CPU usage. Open up system monitor and see if anything is using it up.

---

### Post by ibuclaw on 2009-11-19
> **xxhopingtearsxx said:**
> ```
joey@ubuntu:~$ ls /proc/acpi/*
/proc/acpi/fan:
FAN

```

OK, the Fan appears detected, but not in the way I would usually expect it to be (then again, DSDT implementations vary from vendor to vendor).

Run the following:
```

cat /proc/acpi/fan/*/state
cat /proc/acpi/thermal_zone/*/trip_points
cat /proc/acpi/thermal_zone/*/temperature

```
Lastly, you can see what device it is registered as by running:
```
dmesg | grep -i fan
```
If you see something like:
> [    0.682767] fan PNP0C0B:00: registered as cooling_device0
From that you can check:
```
ls /sys/class/thermal/**cooling_device0**
```
and
```
ls /sys/class/thermal/**cooling_device0**/device
```
To ensure that things such as cur_state, max_state, driver, hid, modalias and path exist.

If all checks out, and is all detected. Then there is nothing much further that you could try to do from a user perspective.
From a developers perspective though, there are tools out there that will allow you to control what temperature the fan should turn on / off. Albeit, at the cost of accidents may happen. (googling 'acer aspire one fan control' will lead you in the right direction of how to do it. But there is no generic way, everything is systemboard dependant, and will require your own investigations into).

If you post the output of the above commands, I can see if there appears to be a problem with fan detection in the ACPI of your machine. If that is the case, there are ways of changing the way Linux treats ACPI and IRQs of devices at boot up - thus may resolve any harmless conflict and allow the fan to be detected/allocated on the system.

Regards
Iain

---

### Post by xxhopingtearsxx on 2009-11-19
I did all of them. I love Ubuntu, but the superfast fan is ruining my experience with Ubuntu. There's hardly anything running that's using up a lot of memory. Processor right now is 5% in use. It's hard to enjoy Ubuntu if I need music to deafen the sounds of cold air rushing from my laptop.

```
joey@ubuntu:~$ cat /proc/acpi/fan/*/state
status:                  on
joey@ubuntu:~$ cat /proc/acpi/thermal_zone/*/trip_points
critical (S5):           114 C
passive:                 114 C: tc1=2 tc2=5 tsp=300 devices=CPU0 CPU1 
active[0]:               70 C: devices= FAN 
joey@ubuntu:~$ cat /proc/acpi/thermal_zone/*/temperature
temperature:             42 C
joey@ubuntu:~$ cat /proc/acpi/fan/*/state
status:                  on
joey@ubuntu:~$ cat /proc/acpi/thermal_zone/*/trip_points
critical (S5):           114 C
passive:                 114 C: tc1=2 tc2=5 tsp=300 devices=CPU0 CPU1 
active[0]:               70 C: devices= FAN 
joey@ubuntu:~$ cat /proc/acpi/thermal_zone/*/temperature
temperature:             42 C
joey@ubuntu:~$ dmesg | grep -i fan
[    3.683625] fan PNP0C0B:00: registered as cooling_device0
[    3.683630] ACPI: Fan [FAN] (on)
joey@ubuntu:~$ ls /sys/class/thermal/cooling_device0
cur_state  device  max_state  power  subsystem  type  uevent
joey@ubuntu:~$ ls /sys/class/thermal/cooling_device0/device
driver  hid  modalias  path  power  subsystem  thermal_cooling  uevent
joey@ubuntu:~$ 

```

---

### Post by Abadon125 on 2009-11-19
Do you know which fan it is?  If it is one on a dedicated graphics card the installing the restricted graphics drivers might help. I have had that happen before I think.

---

### Post by ibuclaw on 2009-11-20
Well, all is detected and fine. So there is nothing more I can really ask you to do.

If you are comfortable with bios programming and analysing hex dumps, be my guest. But I don't think you really want to go down that route.

---

