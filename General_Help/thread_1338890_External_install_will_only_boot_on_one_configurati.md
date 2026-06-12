---
title: "External install will only boot on one configuration."
date: 2009-11-26
forum: General Help
---

### Post by Poisonsting on 2009-11-26
I Have recently installed Karmic 64bit on an external drive using VirtualBox to complete the install. After installation, the first computer that the install boots on becomes the ONLY configuration it will boot on. I have done two different installs, each time booting on a different computer. The first time, I booted it on a Dell from my University's computer lab, and I could switch between any of the computers in the lab, they are all exactly the same. I then went home and wiped my install, installing again and booting on my computer at home, since my config is extremely unique on that machine, it refuses to boot on any other machine at all.

I receive 2 different errors:

Error 1:
```
Gave up waiting for root device. Common problems:
-Boot args (Cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdc1 does not exist. Dropping to a shell!
```

The second error only happened on the first install, so I cannot repeat it, but the general flow of the error was:
```
Cannot mount /dev on /root/dev directory does not exist
Cannot mount /sys on /root/sys directory does not exist
Cannot mount /proc on /root/proc directory does not exist
```
Upon trying to add directories in /root I received a "Failed to create directory Read-Only Filesystem".

Please help! This is driving me nuts!
I'm guessing there is information in a conf file telling the system to mount a pre-determined disk in a pre-determined fashion, blindly, which to my mind is perfect if it's not an external install, but... it is.

Thanks in advance.

---

### Post by cariboo on 2009-11-26
Do you have grub installed on the external drive only?

---

### Post by Poisonsting on 2009-11-27
Yes, as I don't want to be messing with other people's settings, just hijacking the hardware.

---

