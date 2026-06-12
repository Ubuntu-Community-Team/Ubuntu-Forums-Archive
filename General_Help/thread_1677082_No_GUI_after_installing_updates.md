---
title: "No GUI after installing updates"
date: 2011-01-28
forum: General Help
---

### Post by multiman on 2011-01-28
Hi everybody,

I know this problem has been discussed before, but I couldn't solve it using the methods supposed.

First, about my PC and OS:
CPU: AMD Pheneom 3600 MHz
RAM: 8 GB
VGA: Nvidia 450 GTS
Motherboard: Gigabyte 770TA-UD3
OS: Ubuntu 10.10 (Maverick) 32-bit, Gnome

Yesterday (Thursday 27-01-2011), I checked and installed the updates given by Ubuntu. The system then asked for a restart, and I did restart indeed.

Then I was surprised that it didn't start in GUI; it started in console (command prompt ?). I logged in and typed: "startx", just to see this common error message:

```

FATAL: Module nvidia not found
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

/Then it says/
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error

```

I tried many methods, but yet I couldn't solve this issue.

I believe that the problem is between Nvidia driver and the newest updates. I couldn't access my hard drive in /media to reinstall the driver because I have this "permission denied" problem even though I'm a root user.

I couldn't also remove this property driver to load Ubuntu in low graphics mode so I can access to the driver.

I'm stuck now, and I appreciate your help.

Thanks in advance

---

### Post by multiman on 2011-01-28
OK, now I see there are number of users having thin problem. I'll continue with this topic:
[http://ubuntuforums.org/showthread.php?t=1658874](http://ubuntuforums.org/showthread.php?t=1658874)

---

### Post by multiman on 2011-01-28
Finally, I got this problem fixed. And these are the steps just in case somebody faced the same problem:

1) I succeeded booting from "HDD-USB" as Ubuntu startup disc. and choosed "try Ubuntu" option.
2) I downloaded the latest driver from Nvidia website. Then I copied it to my desktop on my original HDD, of course after running the command:
```
sudo chown 'user' /home/'user'/Desktop
```
3) I restarted the PC, and booted from the HDD, just to face the console menu.
4) I accessed successfully to my Desktop and installed the new driver. The installer removed the old one automatically... The command I used to install the new driver is:
```
sudo sh ./NVIDIA-Linux-x86-260.19.36.run
```
You can take it from Nvidia website, I mean the installation line.
5) I restarted the system and, TAADAAAH!

It worked like a charm, luckily.

---

