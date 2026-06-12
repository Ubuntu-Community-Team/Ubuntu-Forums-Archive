---
title: "Fan speed with HDDtemp"
date: 2010-02-25
forum: General Help
---

### Post by lemurid on 2010-02-25
Trying to get those pesky fans under control. I have already set up lm-sensors, together with fancontrol... But i have another 120cm fan blowing over an HDD cage. I can get the readings from hddtemp, but how do i integrate them with fancontrol? Or maybe there is a different program which can take control of the fan based on the HDD temperature readings?

---

### Post by lemurid on 2010-02-26
I have studied the problem and decided to coe up with a small script file. But as i don't have enough knowledge in scripting maybe someon can help with finishing it off? Planning to start it from CRON every 10 seconds


```
#!/bin/bash
clear

# tis is a PWM controller of an HDD fan
path=/sys/class/hwmon/hwmon4/device/pwm1
input1=$(/usr/sbin/hddtemp -n /dev/sda)

echo "1" > ${path}_enable

while [what shall be put here?]; do


read input1
#We take PWM 100 as a silent fan mode
if [ $input1 <= 35 ]; then
  echo "100" > $path
fi
#PWM 255 stand for maximum fan speed mode
if [ $input1 > 36 ]; then
  echo "255" > $path
fi


then
exit 1
fi
done
```

---

### Post by cjhabs on 2010-02-26
If you are running it from cron then I don't see a need for a while loop.
If you were just to run the script, no cron, I would do:
while 1
and then add a "sleep 10" to sleep for 10 seconds.

---

