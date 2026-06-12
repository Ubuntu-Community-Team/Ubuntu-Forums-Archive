---
title: "Reduce Power / Power Saving"
date: 2010-07-05
forum: General Help
---

### Post by kenm_uk on 2010-07-05
I have a media/file/subversion server which I run 24/7 at home. I was wondering what tips people have for reducing the power consumed by this machine.

I have a voltage meter attached to the plug of the machine which lets me see how much power it uses.  My machine is an AMD Phenom 9550 with 2 hard drives and a DVD drive.  It runs at 125 watts when booting and under load and will often idle around 80 watts.

I have seen some sites with tips on reducing power consumption but many of the web pages are quite old.  For instance, I have one of the newer "green" drives installed on the machine ([http://www.ebuyer.com/product/183971](http://www.ebuyer.com/product/183971)).  Is there anything I need to do to ensure the drive enters the low power state?

Does anyone else have any tips on reducing power consumption?  How do I know if the hard drives have gone into a low-power/idle mode?  Is there a way to change the settings so they are more likely to go into an idle state?  Is there a way to put the onboard graphics card to sleep and does this save power?

Thanks.

---

### Post by Xianath on 2010-07-05
By far the largest power hog in this box is the CPU. You can cut the power in half by switching to a 45W quad-core as the Athlon II X4 610e, or if you really need the L3 cache, a 65W quad-core such as the Phenom II X4 910e.

A green drive will save you about 4W as compared to a regular desktop drive. Unless you run a dozen of these (which assumes RAID for which they are completely unsuitable), they're not worth considering except that it keeps cooler.

Also, if you have such low load on your box, get a good (80+ certified) 200-250W PSU. It will be more efficient than a 600W running almost idle. The FSP220-60LE(80) even comes with Active PFC.

---

### Post by warfacegod on 2010-07-05
If you have a swap partition, you might consider reducing the swapiness. That will reduce HDD use but I doubt it will save all that much power. Maybe a couple of watts over the course of a day.

---

### Post by kenm_uk on 2010-07-05
> **Xianath said:**
> By far the largest power hog in this box is the CPU. 

Thanks for all the tips. Is there a way to reduce the power consumed by my existing processor? For instance, can I force the processor to run at a lower clock speed or for it to at least try to remain at a lower speed unless the load is quite high?

---

### Post by kenm_uk on 2010-07-05
> **warfacegod said:**
> If you have a swap partition, you might consider reducing the swapiness. That will reduce HDD use but I doubt it will save all that much power. Maybe a couple of watts over the course of a day.

Good tip. I have already set swappiness from the default 60 to 10.

---

### Post by Xianath on 2010-07-05
You can underclock it and undervolt it: [http://forums.overclockers.com.au/showthread.php?t=724191](http://forums.overclockers.com.au/showthread.php?t=724191)

---

### Post by khelben1979 on 2010-07-05
If you have a monitor connected to it, there is very power efficient ones available today.

Other than that, the type of power supply you have is very important in measuring how much power it consumes. Better to not fixate on total wattage it can handle and focus on it's efficiency levels.

Read over at [www.hardwareheaven.com](www.hardwareheaven.com) in reviews on powersupplies for more information. Pretty good tests.

---

### Post by happyhamster on 2010-07-05
> **kenm_uk said:**
> Thanks for all the tips. Is there a way to reduce the power consumed by my existing processor? For instance, can I force the processor to run at a lower clock speed or for it to at least try to remain at a lower speed unless the load is quite high?
- The "ondemand" cpu-frequency scaling governor does exactly that. Ubuntu has several such governors: on a desktop the default is usually "performance" (the cpu always runs at the highest available frequency).

- You can change the governor using the CPU Frequency Scaling Monitor (right-click the top panel-->Add to Panel-->CPU Frequency Scaling Monitor). Note that you have to set all cores separately (which is a bit of a pain). The settings also won't stick after a reboot.

- Another (permanent) way is to edit the file /etc/rc.local: the commands you add to this file will be run once during bootup.

gksudo gedit /etc/rc.local

- It should look like this:
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

exit 0

```

- For a quadcore cpu, make it look like this:

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

sleep 10

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor

exit 0

```
- Save, and exit the text editor. Reboot. Note that the "sleep 10" part is needed to make sure the commands are run *after* the necessary modules are loaded. Good luck

---

### Post by Xianath on 2010-07-05
CPU frequency scaling is good but undervolting is even better. The Phenom doesn't scale down its core voltage when not under use. Given this box's usage profile, the CPU will run at its lowest frequency almost all the time. With that, I think manually underclocking AND undervolting should yield the most power savings while leaving more than enough performance for the box to operate normally (unless it transcodes HD). My heart bleeds at the though of crippling a great CPU that way but hey, it's for the environment (and the power bills) :)

---

### Post by kenm_uk on 2010-07-07
Thanks for all the tips.

> The "ondemand" cpu-frequency scaling governor does exactly that. Ubuntu has several such governors: on a desktop the default is usually "performance" (the cpu always runs at the highest available frequency).

When I run 
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
ondemand

```

So it appears Ubuntu has set up my box to use on-demand.

Under-clocking does seem like a good option. My main hesitation there is that I suffered from a mouse-freeze problem when I initially set up my box ([http://ubuntuforums.org/showthread.php?t=1338700](http://ubuntuforums.org/showthread.php?t=1338700)) and through various trial and error I finally got the bios settings correct so that the box works fine.  My fear is that having to do a CMOS reset will set me up for another weekend of trial and error to fix it (although I think the solution was to disable the HPET).

Is there much chance of damaging the anything by trying to underclock the machine?

Thanks,
Ken

P.S. In case anyone is reading my posts in other threads I have two machines:
1) Phenom 9950 (2.6GHz) with Gigabyte motherboard
2) Phenom 9550 (2.3GHz) with Asus M3N-H/HDMI
and it is the former that is my HTPC/field server which I want to run in low power mode and the latter is desktop.  I know, I really should be swapping the processors.

---

