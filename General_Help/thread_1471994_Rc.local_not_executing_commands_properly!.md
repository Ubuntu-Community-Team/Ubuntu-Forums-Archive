---
title: "Rc.local not executing commands properly!"
date: 2010-05-04
forum: General Help
---

### Post by Mixalis0 on 2010-05-04
Here is my /etc/rc.local in both Jaunty and Lucid:

```
#!/bin/sh -e
#
# rc.local

echo "rc.local start ok" > /tmp/check-rclocal

# Switches ESC and CAPS in virtual console
(echo `dumpkeys |grep -i keymaps`; echo keycode 58 = Escape) | loadkeys
(echo `dumpkeys |grep -i keymaps`; echo keycode 1 = Caps_Lock) | loadkeys

echo "rc.local checkpoint 1 ok" >> /tmp/check-rclocal

# Adjusts Trackpoint speed
echo -n 200 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity

echo "rc.local finish ok" >> /tmp/check-rclocal

exit 0
```The very peculiar problem is that Jaunty makes it to "rc.local finish ok" without error (and sets the trackpoint options successfully), but Lucid does not! In Lucid, /etc/rc.local only makes it as far as "rc.local checkpoint 1 ok."

To make it even more perplexing, when I run in Lucid ```
sudo /etc/rc.local start
``` everything works just fine.

Any insight? Thanks!

---

### Post by john newbuntu on 2010-05-04
A timing issue perhaps?  Remember that upstart takes over in the newer versions.  So at the time of running of your script, it is possible that the device is not ready yet.  Introduce a sleep (example: sleep 60) in your script after checkpoint 1 and see if that helps in Lucid.

I think the better way to configure options like speed and sensitivity in post Jaunty systems would be to use udev.  You need to create a rules for your trackpoint in a file and place them in /etc/udev/rules.d/.
Or install the gpointing-device-settings package and configure it graphically.

---

### Post by Mixalis0 on 2010-05-04
Good call on the timing issue. It looks like that in Jaunty, /etc/rc2.d/S24hal initialized devices in advance of /etc/rc2.d/S99rc.local; thus, replacing the speed and sensitivity files in rc.local made sense. However, as you pointed out, Lucid uses udev instead of HAL, so the devices aren't initialized before rc.local is executed. Now I just have to work out an appropriate udev rules file. (I'll post what I come up with in case anyone else is curious.) Thanks.

---

### Post by Mixalis0 on 2010-05-05
Okay, to remedy this, I installed [sysfsutils]("http://linux-diag.sourceforge.net/Sysfsutils.html") (sudo apt-get install sysfsutils) and then appended the following lines to my /etc/sysfs.conf:

```
devices/platform/i8042/serio1/serio2/speed = 200
devices/platform/i8042/serio1/serio2/sensitivity = 255
```

This looks like the most efficient way to configure the Trackpoint.

---

