---
title: "Lucid Linux Freezing"
date: 2011-01-07
forum: General Help
---

### Post by DinoT1985 on 2011-01-07
Hi, yesterday I downloaded the latest updates that Ubuntu told me were new. Before that the last update was about 2 weeks ago.

Now my CPU meter will go off the scare, as well as my cache and everything goes darker until the computer catches up with whatever it has to do. This is just with browsing the web.

Earlier it also said my disk only had 1. something GB left which cant be right since its 250GB and i literally have 14GB worth of files on it.

I'm still learning Ubuntu, so please bare with me. How can I view a log of what got downloaded? That way I can see about reverting to the older versions which I had no problem with. I am currently booted in Windows 7.

---

PC Info:

**Operating Systems**
    MS Windows 7 Ultimate 64-bit
    Ubuntu 10.04 amd64
**CPU**
    Intel Mobile Core 2 Duo P8400  @ 2.26GHz    41 °C
    Penryn 45nm Technology
**RAM**
    4.0GB Dual-Channel DDR2 @ 399MHz (6-6-6-18)
**Motherboard**
    Compal 30F4 (CPU)
**Graphics**
    Generic PnP Monitor @ 1440x900
    512MB GeForce 9600M GT (HP)    79 °C
**Hard Drives**
    244GB Hitachi Hitachi HTS543225L9A300 ATA Device (SATA)    45 °C
    244GB Hitachi Hitachi HTS543225L9A300 ATA Device (SATA)    38 °C
**Optical Drives**
    Optiarc BD ROM BC-5500S ATA Device
**Audio**
    IDT High Definition Audio CODEC

---

### Post by Krytarik on 2011-01-07
The log of apt is stored in "/var/log/apt/history.log".

Check with
```
df -h
```
in a terminal, if there is really enough disk space left.

---

### Post by DinoT1985 on 2011-01-07
Thank you.

My log

> Start-Date: 2011-01-07  11:03:19
Upgrade: 
libapparmor-perl (2.5.1-0ubuntu0.10.04.1, 2.5.1-0ubuntu0.10.04.2), 
apparmor-utils (2.5.1-0ubuntu0.10.04.1, 2.5.1-0ubuntu0.10.04.2), 
ifupdown (0.6.8ubuntu29.1, 0.6.8ubuntu29.2), 
dpkg (1.15.5.6ubuntu4.4, 1.15.5.6ubuntu4.5), 
dpkg-dev (1.15.5.6ubuntu4.4, 1.15.5.6ubuntu4.5), 
libapparmor1 (2.5.1-0ubuntu0.10.04.1, 2.5.1-0ubuntu0.10.04.2), 
apparmor (2.5.1-0ubuntu0.10.04.1, 2.5.1-0ubuntu0.10.04.2), 
emesene (1.6.1-0ubuntu1, 2.0.21~ppa2~ubuntu1)
End-Date: 2011-01-07  11:11:59Would any of these cause the problems I listed?

I cant run terminal, now if I open it up or any window I dont get any contents, not even buttons. Just the background colour being all over.

result of df -h, i am now running in failsafe low graphics mode.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G   31G  179G  15% /
none                  2.0G  340K  2.0G   1% /dev
none                  2.0G  1.2M  2.0G   1% /dev/shm
none                  2.0G  252K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw

---

### Post by Krytarik on 2011-01-07
I don't think that any of the updated packages is able to cause the behaviour you are experiencing.

Though it seems caused by the updates, it's more likely a video driver issue.

First I recommend updating all installed packages, the update manager only takes care of security updates:
```
sudo apt-get update
sudo apt-get upgrade

```Second, what a video driver do you use, how installed?

---

### Post by Krytarik on 2011-01-07
> **DinoT1985 said:**
> 
**Graphics**
    Generic PnP Monitor @ 1440x900
    512MB GeForce 9600M GT (HP)    79 °C

Is your card really that hot (in the bad way ;-))?

EDIT: After doing a web search on that, it seems it's normal for video cards to reach such high temps, I didn't know that. You really shouldn't put your fingers on it while running! ;-)

---

### Post by DinoT1985 on 2011-01-07
this is after the upgrade

dino@dino-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am using the recommended NVIDIA driver via the Hardware Drivers tool.

yeah this is a laptop that i use for work. i am an imedia designer so i use it for video editing, high graphics creation, game design etc. so it gets pretty heated.

---

### Post by Krytarik on 2011-01-07
Try just setting the "driver" in the "Device"-section of "/etc/X11/xorg.conf" from "nvidia" to "nv", the open source -non hw-accel capable- driver gets used then.

---

### Post by Krytarik on 2011-01-07
> **Krytarik said:**
> the update manager only takes care of security updates
Seems that I've missinterpreted a recent post in the forums, it's like that instead:
> Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by DinoT1985 on 2011-01-07
> **Krytarik said:**
> Try just setting the "driver" in the "Device"-section of "/etc/X11/xorg.conf" from "nvidia" to "nv", the open source -non hw-accel capable- driver gets used then.

tried that, still nothing. I'm just gonna do a clean install if I can or stick with Windows 7. I updated to 10.10 a while ago and these problems happened, so I reinstalled 10.04. I guess the updates just dont go with my hardware. I dont understand how those yupdates could have messed things up.

---

### Post by Krytarik on 2011-01-07
> **DinoT1985 said:**
> tried that, still nothing. I'm just gonna do a clean install if I can or stick with Windows 7. I updated to 10.10 a while ago and these problems happened, so I reinstalled 10.04. I guess the updates just dont go with my hardware. I dont understand how those yupdates could have messed things up.
Me neither, I just installed exactly those updates after my previous post, and everthing is as it used to be, fortunately.;-)

---

