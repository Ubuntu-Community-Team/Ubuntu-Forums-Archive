---
title: "Thermal Readouts"
date: 2009-08-16
forum: General Help
---

### Post by RedSingularity on 2009-08-16
Anyone have any suggestions on how to get thermal readings from the computer components?  Things like the CPU and the Graphics Card.  HDD is not really that essential.  By the way it can be software or hardware.   Thanks.

---

### Post by earthpigg on 2009-08-16
```
sudo apt-get install lm-sensors

sudo sensors-detect
```

then, to see your cpu temp:
```
sensors
```

---

### Post by Rocket2DMn on 2009-08-16
"hddtemp" is used to check the temperature on hard disks, and it is available in the repos.  To use it:
```
sudo hddtemp /dev/sda
```
where sda is the device (note the absence of a partition number).

There are also panel applets in Gnome that can be used for such things, like a CPU frequency scaling applet, and another which needs to be installed called "sensors-applet".  It is called Hardware Sensors Monitor in the applet listing.

---

