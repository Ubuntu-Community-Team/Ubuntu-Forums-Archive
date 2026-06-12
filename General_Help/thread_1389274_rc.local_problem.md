---
title: "rc.local problem"
date: 2010-01-24
forum: General Help
---

### Post by jrdm on 2010-01-24
Hello!

My Cpu always boot up at "performance" mode. I tried to change on cpu scaling frequency to On demand but it simply does nothing.
So i searched at /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq and i've checked out that the scaling_min_freq its at 1833000 which is my max_freq!!!

if i've change that value to 1000000, every thing becomes ok. But after i reboot, the min value changes again to 1833000.

So i tried to change the rc.local but when i reboot no changes are made and the freq problem remains! What am i doing wrong?

My rc.local file:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo "11:19 8:19 6:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "11:19 8:19 6:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo 1000000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
echo 1000000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq

exit 0
```

the output for ls -lh /etc/rc.local is:

```
-rwxr-xr-x 1 root root 734 2010-01-24 11:57 /etc/rc.local

```

thanks and sorry but i'm a newbie :(

---

### Post by jrdm on 2010-01-24
oh come on! help anyone plz!

---

### Post by jrdm on 2010-01-24
bump

---

### Post by bodhi.zazen on 2010-01-24
I believe your problems is "concurrency"

To speed boot times, boot scripts are run concurrently.

So your commands are running from rc.local before /sys is mounted 

The easiest solution is to add a sleep to rc.local, right before your commmands

sleep 10

is usually sufficient.

Your other options are to modify the upstart scripts.

---

### Post by jrdm on 2010-01-24
Thanks, but now i think that the problem it's a little bit bigger.
i tought that the configuration at scaling_min_freq and scaling_governator was just no booted up as i want, but now i realised that somehow this configuration files are changed without i do nothing to "performance" and to the max freq value.
I echo a diferent freq value at scaling_min_freq, but minutes it returns to the value that was before!

conclusion: i have allways the cpu at max_freq value and at "performance" mode. And i not able to change using scaling monitor panel, only using echo (and it only works for a few minutes)

anyone have any idea?

---

