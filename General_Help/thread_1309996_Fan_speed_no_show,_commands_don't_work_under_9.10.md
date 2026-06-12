---
title: "Fan speed no show, commands don't work under 9.10?"
date: 2009-11-01
forum: General Help
---

### Post by blackSP on 2009-11-01
Under 9.04 I had all these nice stats (core, hdd & gpu temp, fan speeds, voltages) running in my panel using lm-sensors and sensors-applet.

Now under 9.10 I'm not getting it to work anymore.

I'm running an Asus P5QL-E MoBo with Samsung drives, Core2Duo E7600 and 2 case fans.
Basically I installed both packages and dependencies.

'sensors detect' runs fine
I add to /etc/modules:
coretemp
w83627ehf force_id=0x8860

I then try to load this into the kernel by typing:
sudo /etc/init.d/module-init-tools

This results into this:
user-desktop:~$ sudo /etc/init.d/module-init-tools
Usage: /etc/init.d/module-init-tools COMMAND
user-desktop:~$ sudo /etc/init.d/module-init-tools COMMAND
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools COMMAND

The script you are attempting to invoke has been converted to an Upstart
job, but COMMAND is not supported for Upstart jobs.

This also gives an unexpected result:
user-desktop:~$ sudo modprobe w83627ehf force_id=0x8860
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting w83627ehf (/lib/modules/2.6.31-14-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

Oh, I have been following this guide (and others): [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)


Any ideas???

---

### Post by blackSP on 2009-11-02
Bump

---

### Post by blackSP on 2009-11-02
Bump?
bbbbbbump....

---

### Post by blackSP on 2009-11-04
Really, is there nobody that ran into this same problem and has a solution?
Or can point me in the right direction?

I've been looking for clues for a few days now and tried a bunch of things but no go so far.

Anybody with an Asus P5 mobo running Ubuntu 9.10 got their fan speed in the sensors applet going? Please tell me...

---

### Post by blackSP on 2009-11-05
Crap, am I just spamming or what?

---

### Post by DeMus on 2009-11-05
Same here. I have a P5K motherboard and was also missing some sensors. It's because of the kernel. When i was using Jaunty (which I am using again now) I also switched to the latest kernel 2.6.31 and had this problem in Jaunty. Going back to 2.6.30 solved those problems.
So it is no Ubuntu, it is the kernel which has a bug.
You can try to install kernel 2.6.30 but be prepared to have other problems. I did it and lost my sound. So I installed Jaunty again and keep using it until the next LTS release.

---

### Post by blackSP on 2009-11-05
Hi musje, thanks, finally a useful pointer. I guess I'll better wait until the next kernel update then!

---

### Post by VyacheslavS on 2009-12-23
> **blackSP said:**
> Hi musje, thanks, finally a useful pointer. I guess I'll better wait until the next kernel update then!

I've got Asus p5b. I did so:
download the new libs from Debian
[http://packages.debian.org/sid/lm-sensors](http://packages.debian.org/sid/lm-sensors) (lm-sensors 1:3.1.1-4)
[http://packages.debian.org/sid/libsensors4](http://packages.debian.org/sid/libsensors4) (libsensors4 1:3.1.1-4)

and have installed their.
**Now everything is OK!**
All temperature and voltage, I see. Speed of the fans also displayed. :)

---

