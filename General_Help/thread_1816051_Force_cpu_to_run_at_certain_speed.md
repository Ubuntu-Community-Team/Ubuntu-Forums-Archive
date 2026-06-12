---
title: "Force cpu to run at certain speed"
date: 2011-08-01
forum: General Help
---

### Post by dtrot55 on 2011-08-01
I have a Dell Inspiron 9200 with the Intel Pent M 1.8ghz processor that has speed stepping.  For some reason the speed stepping doesn't seem to be working...is there a way for me to force the CPU to run at a higher speed then the current 600mhz...I installed cpufreq but the commands i give it from the cpufreq wiki don't seem to be doing much.  Anyone have any other ideas???

---

### Post by CatKiller on 2011-08-01
It probably is working and you just aren't pushing your computer that hard. My processor very rarely goes above its minimum speed.

Adding "CPU Frequency Scaling Monitor" to the Panel is the easiest way I've found of controlling this behaviour. It lets you set a speed, or just change the profile for how aggressive the underclocking is.

---

### Post by dtrot55 on 2011-08-01
Thanks for the reply...yeah I opened the monitor and opened up my justin.tv stream in chrome, which struggles to even run, and my CPU speed didn't increase over 600mhz...I tried adding the cpu thing to the panel but I do not see it as an option

---

### Post by CatKiller on 2011-08-01
It's possible that it was called something else in Lucid, I really can't remember. I believe that Xubuntu uses the same panel & applets as Ubuntu, though (hadn't spotted that part of your post earlier).

Actually, I just checked, and it isn't the same panel. There is xfce4-cpufreq-plugin which may do the same thing, though.

There is an AWN applet that also does the same thing, if you use AWN. Otherwise, it's probably doing things properly, which I don't have a lot of experience of :)

---

### Post by TBABill on 2011-08-01
Did you already try ```
sudo cpufreq-set --cpu 0 --governor performance
``` and do the same for CPU 1, 2, 3....whatever your system has. Most have only 0 and 1 or just 0.

---

### Post by dtrot55 on 2011-08-01
Thanks Cat...I downloaded that plugin...but doesn't seem to actually change the speed when i set it....and thanks TBABill...I tried your code...looks like the performace stuck but its still just chilling at 600mhz :(

---

### Post by CatKiller on 2011-08-01
> **dtrot55 said:**
> but doesn't seem to actually change the speed when i set it....

You can probably turn off SpeedStep in the BIOS.

---

### Post by dtrot55 on 2011-08-01
Turning off speed step forces cpu to run at lowest possible speed..but will give it a try

---

### Post by CatKiller on 2011-08-01
Really? I'd have expected it to be the other way. Worth a try, though.

---

### Post by dtrot55 on 2011-08-01
Yeah it forced it down...guess Xubuntu isn't the way to go then...I remember Ubuntu allowing the cpufreq to work ... so might have to go back

---

### Post by Toz on 2011-08-01
11.04 uses an ondemand service to manage cpu governance. Unfortunately, its currently in a semi-broken state - not allowing you to permanently change the governor setting from userspace. However, if you want it to run with a different governor setting than its default (default=ondemand), you can make a change directly to the startup file. Edit the file **/etc/init.d/ondemand** ```
gksudo mousepad /etc/init.d/ondemand
```and change the line that reads:
> echo -n ondemand > $CPUFREQ
to
```
echo -n _governor_ > $CPUFREQ
```
where _governor_ is one of:
> $ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance

Then reboot.

To have the cpu's run at a performance setting, the line should read:
```
echo -n performance > $CPUFREQ
```

EDIT: Here's a launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/709390]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/709390")

---

