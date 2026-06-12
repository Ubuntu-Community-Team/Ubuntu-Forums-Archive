---
title: "fancontrol/pwmconfig/sensors, sysfs?"
date: 2006-06-20
forum: General Help
---

### Post by seedoubleyou on 2006-06-20
I am trying to get my fans to stop running at full throttle as my family and I are on the cusp of deafness.  I have installed fancontrol/pwmconfig/sensors/sensord, however pwmconfig or fancontrol appear to be unable to successfully write to anything under the /sys partition on my Dapper 6.06 LTS partition.

Here is the error output on first running pwmconfig:

Found the following PWM controls:
   0-002e/pwm1
/usr/sbin/pwmconfig: line 102: 0-002e/pwm1_enable: Permission denied
   0-002e/pwm2
/usr/sbin/pwmconfig: line 102: 0-002e/pwm2_enable: Permission denied
   0-002e/pwm3
/usr/sbin/pwmconfig: line 102: 0-002e/pwm3_enable: Permission denied

It would appear nothing is able to modify the files located in SDIR=/sys/bus/i2c/devices , and it would appear DIR=/proc/sys/dev/sensors
 doesn't even exist.

'mount' output says that /sys is mounted as sysfs with rw permissions, yet I cannot even modify these files as root user.

any ideas?  help?

---

