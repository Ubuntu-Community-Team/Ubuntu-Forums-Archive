---
title: "thinkfan only has full speed or off"
date: 2011-02-08
forum: General Help
---

### Post by qwertyjjj on 2011-02-08
I have had to disable speedstep in my BIOS as there is something wrong with it. I think either the thermal sensor is faulty or something is causing the cpu to lock down to 800.

As soon as I disabled speedstep, the computer now runs at 1.73GHz correctly but the fan comes onto full speed as soon as Ubuntu is loaded. The temperature is only between 45-55oC.
So, I installed thinkfan and set the conf to:
(0,    0,      55)
(1,    55,     60)
(2,    60,     65)
(3,    65,     70)
(4,    70,     75)
(5,    75,     80)
(7,    80,     32767)

However, the fan comes onto full speed, there doesn;t seem to be a middle setting even though I have heard the fan on low speed previously.
Any ideas on what I can do to help this?

The fan right now is on 140000RPM and doesn;t need to be as the temp is only 30oC

I get all the following errors:
jason@jason-Inspiron-9300:/proc/acpi/fan$ thinkfan -c /etc/thinkfan.conf

WARNING: Using default temperature inputs in /proc/acpi/ibm/thermal.
WARNING: You have not provided any correction values for any sensor, and your fan will only start at 60 °C. This can be dangerous for your hard drive.
Config as read from /etc/thinkfan.conf:
Fan level	Low	High
 0		0	60
/proc/acpi/ibm/fan: No such file or directory
Error opening /proc/acpi/ibm/fan. Is this a computer really Thinkpad? Is the thinkpad_acpi module loaded? Are you running thinkfan with root privileges?
jason@jason-Inspiron-9300:/proc/acpi/fan$

EDIT: apparentlly I have to use the hwmon interface for this but I cannot find the path to the fan.
The example says fan /sys/class/hwmon/hwmon3/device/pwm1 but this doesn't exist in meerkat

---

### Post by tgalati4 on 2011-02-08
What model of computer?
Are you running thinkfan with sudo?

---

### Post by qwertyjjj on 2011-02-08
> **tgalati4 said:**
> What model of computer?
Are you running thinkfan with sudo?

I just installed it and changed the conf, it should run automatically at startup.
DELL Inspiron 9300.

Am trying that but the path to fan in the example does not exist in maverick meerkat.
What should I use?

sensor /sys/class/hwmon/hwmon0/temp1_input
#    fan /sys/class/hwmon/hwmon3/device/pwm1 - this folder/file does not exist in meerkat
(0,	0,	55)
(36,	48,	60)
(72,	50,	61)
(109,	52,	63)
(145,	56,	65)
(182,	59,	66)
(255,	63,	32768)

I have something called i8kfan in /usr/bin/i8kfan - could that be it? [http://www.diefer.de/i8kfan/](http://www.diefer.de/i8kfan/)

---

### Post by qwertyjjj on 2011-02-08
I have got i8k working instead of thinkfan.

I can manually control the fan speed but i8k is supposed to do it automatically yet when I manually turn the fan off, it does not come on when the temp gets above 55.
I have i8k add to the /etc/modules file.

This is the conf:

```

# Run as daemon, override with --daemon option
set config(daemon)      0

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)	1

# Status check timeout (seconds), override with --timeout option
set config(timeout)	1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{-1 0}  -1  55  -1  55}
set config(1)   {{-1 1}  55  70  55  70}
set config(3)   {{-1 2}  70  128  70  128}

# For computer with 2 fans, use a variant of this instead:
# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# set config(0)	{{-1 0}  -1  52  -1  65}
# set config(1)	{{-1 1}  41  66  55  75}
# set config(2)	{{-1 1}  55  80  65  85}
# set config(3)	{{-1 2}  70 128  75 128}

# end of file

```

Anything else I can try?
The distro is maverick meerkat.
BTW, I some some warning somewhere that i8k needed a conf file and it would not be updated - what's that about?

---

### Post by gordintoronto on 2011-02-08
I would install lm-sensors.

By the way, why do you want it to run constantly at 1.73 GHz? Most of the time it's sitting there waiting for you to press a key or move the mouse, and 800 MHz is plenty fast enough!

I consider anything over 50 degrees to be "hot."

---

### Post by qwertyjjj on 2011-02-08
> **gordintoronto said:**
> I would install lm-sensors.

By the way, why do you want it to run constantly at 1.73 GHz? Most of the time it's sitting there waiting for you to press a key or move the mouse, and 800 MHz is plenty fast enough!

I consider anything over 50 degrees to be "hot."

I have a problem with the BIOS or a temperature sensor at present.
After 30mins it throttles to 800 and locks it there. The guys who makde cpufreqd can't figure it out and say it must be the bios.
So, my only option was to turn off speedstep and have it run at 1.73.
However, when it runs at 1.73 the fan starts at full speed, so now I need to control the fan.

---

### Post by qwertyjjj on 2011-02-08
The fan comes on correctly but when the temp drops below 43 it won;t switch off:

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
#set config(0)   {{-1 0}  -1  50  -1  50}
#set config(1)   {{-1 1}  45  70  45  70}
#set config(3)   {{-1 2}  70  128  70  128}

set config(0)   {{1 0}  -1  50  -1  50}
set config(1)   {{1 1}  43  60  43  60}
set config(2)   {{1 2}  50  70  50  70}
set config(3)   {{1 2}  50 128  50 128}

Also, how can I control the GPU fan with i8kmon, there doesn't seem to be an option that will do anything...it only controls the cpu fan.

---

