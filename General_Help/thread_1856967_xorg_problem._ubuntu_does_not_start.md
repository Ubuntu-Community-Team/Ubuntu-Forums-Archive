---
title: "xorg problem. ubuntu does not start"
date: 2011-10-09
forum: General Help
---

### Post by juanvi on 2011-10-09
Hello,

Ubuntu does not start. I get this mesage (translated from Spanish):

Ubuntu is working at a row resolution mode
The following errors were found. You may need to update your configuration in order to solve them.

(EE) [drm] failed to open device
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I have tried to reboot in a failsafe mode but it does not start either.

I am attaching /var/log/Xorg.0.log just in case it helps.

Thank you in advance,

---

### Post by azmyth on 2011-10-09
When you get to the command prompt, you can edit your /etc/X11/xorg.conf with nano and change driver from nvidia to nv then reboot.

---

### Post by juanvi on 2011-10-09
Thanks azmyth,

There is no xorg.conf, just xorg.conf.failsafe and a couple of xorg.conf backups.
Driver "nvidia" only appears in the backups.

I have renamed the last backup as xorg.conf and changed "nvidia" by "nv" and rebooted. Once it reboots I get the same error message :(

---

### Post by azmyth on 2011-10-09
From the command line remove, the xorg.conf since this didn't work then from the command line install the nvidia drivers

apt-get install nvidia-current

then reboot.

---

### Post by juanvi on 2011-10-09
Thanks again. Right now I'm away from that computer. I will try your suggestion as soon as possible.
BTW I believe this problem started after updating something from the Common UNIX Printing System :confused:

---

### Post by azmyth on 2011-10-09
I thought you had a new install. Probably my last post won't help. I'd try to backout the packages you installed that caused the problem. You can view these by looking into the /var/log/dpkg.log file.

---

### Post by juanvi on 2011-10-10
Hi,
I tried first deleting xorg.conf and installing nvidia-current and didn't work.

Then I removed libcups2-dev and libcupsimage2-dev and didn't work either.

From /var/log/dpkg.log it seems that the day it was screwed up was 2011-08-11 (yes, it hasn't been working for a while) and many packages were installed that day. I have attached the dpkg.log. Does any of these packages installed that day ring a bell to you or to somedy else to be the one causing the problem?

Thank you,

---

### Post by juanvi on 2011-10-10
I have removed libqt4 and cups and then done: apt-get autoremove, then rebooted and ubuntu desktop has appered!! have not been able to log in though, it was not acepting my password. 
Then I rebooted again and have found the previous problem, no desktop and the same error mesage I reported in my first post

---

