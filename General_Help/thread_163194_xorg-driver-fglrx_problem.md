---
title: "xorg-driver-fglrx problem"
date: 2006-04-20
forum: General Help
---

### Post by toran on 2006-04-20
OK, I have an older version of this driver installed and working. I want to upgrade to a newer version, so I ran "apt-get install xorg-driver-fglrx". Unfortuantely, it doesn't work- apt exits with the following error:

Preconfiguring packages ...
(Reading database ... 173063 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.16.20-1 (using .../xorg-driver-fglrx_8.22.5-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_8.22.5-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libGL.so.1.2', which is also in package libgl1-mesa
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_8.22.5-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help.

---

### Post by jazzmuzik on 2006-04-20
Why upgrade? I installed the latest version and the screensaver causes X to crash. So I disabled the screensaver, but if the screensaver at the login prompt starts it also crashes. Can't do anything but reboot (although logging in via remote ssh may be possible). And I'm not sure how to disable that screensaver. It's ridiculous that ATI and Nvidia are doing things this way. If you have things working, consider not upgrading.

---

### Post by toran on 2006-04-22
I need the upgrade because a game I want to run won't run with the current drivers. I'm hoping an upgrade will fix the problem.

---

