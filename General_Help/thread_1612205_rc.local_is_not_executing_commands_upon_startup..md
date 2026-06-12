---
title: "rc.local is not executing commands upon startup."
date: 2010-11-02
forum: General Help
---

### Post by ph4z0n17 on 2010-11-02
Hello all,

I am using a Thinkpad T500. Right now, I'm trying to configure the trackpoint on my thinkpad to adjust tthe speed and sensitivity of the device. I made adjustments to the rc.local script, which is as follows:

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

echo $(date) - Running >> /var/test.run

x='/sys/devices/platform/i8042/serio1/serio'
y=2

while [ ! -d "$x$y" ]
do
    y=`expr $y + 1 `
done


sudo  echo -n 120 > "$x$y"/speed
sudo  echo -n 250 > "$x$y"/sensitivity

exit 0
```Now, the issue is, the script does not work upon startup. I can execute the script manually, and it works well then, but when it comes down to actually making the script run by itself upon startup or reboot, I have no luck there. So, can anyone elaborate as per what I'm doing wrong?

---

### Post by ph4z0n17 on 2010-11-02
If it makes any difference, I'm using ubuntu 10.10., 64bit.

---

### Post by prokher on 2010-12-09
I have thinkpad and would like to set up sensitivity and speed from rc.local too. But in my case it definitely executes (checked by touch'ing /home/myname/somefile) but speed and acceleration settings are not applied by some reason.

---

### Post by prokher on 2010-12-09
The interesting thing I've just figured out is that if I put "touch somefile" into rc.local then acceleration and speed settings are applied, otherwise they aren't. Is that special kind of magic? ;)

---

