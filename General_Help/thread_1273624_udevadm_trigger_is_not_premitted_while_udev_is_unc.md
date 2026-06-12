---
title: "udevadm trigger is not premitted while udev is uncongifured"
date: 2009-09-23
forum: General Help
---

### Post by CWG2 on 2009-09-23
I'm about as much of a n00b as can be when it comes to this.  A friend of mine helped me uninstall windows XP and install jaunty.  Worked fine for about an hour but then the computer froze up while i was installing updates for it and I had to shut it off by holding down the power button.  Now it won't boot up anymore.  When i turn it on I get this:
 
udevadm trigger is not premitted while udev is unconfigured.
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/05d79451-0ad0-43fc-9f51-a2c98b4831f2 does not exist.
Dropping to a shell!
 
Apparently another friend of mine burned the disk I used to install it off of limewire so I figure that it was corrupted.  I have a new live CD that should work.  How do I go about fixing this?

---

### Post by xzased on 2009-09-25
For all of you having this prob. I found a thread a while back ago. This fixed my issue after upgrading karmic on 09/24/09. You must chroot to your install using a live cd. After this, you enter:

```
aptitude reinstall udev

```
then

```
initramfs-update -u -k all
```

---

### Post by GreanTee on 2009-11-01
The correct command is 

**update-initramfs** -u -k all

---

