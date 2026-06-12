---
title: "No screens found when trying to start X server"
date: 2010-10-14
forum: General Help
---

### Post by l4nd0fc0nfu510n on 2010-10-14
Running Ubuntu 10.10 x64, fully updated kernel and stuff, in VMWare Workstation 7.

Before I tried installing the Nvidia driver, I set up all my stuff, settings, etc. Restarted several times, everything went okay.

I then decided to install the Nvidia drivers for my GTS 250. I first tried the manual install (sudo sh NVIDIA-INSTALL-NAME.run) and it failed saying something about the nvidia.ko or nvidia.so. I tried using this page [http://ubuntuforums.org/showthread.php?p=9203671](http://ubuntuforums.org/showthread.php?p=9203671) to fix it, but it still failed, so then I used the automatic method (sudo apt-get install nvidia-current) and it installed fine, then I ran nvidia-xconfig and restarted. 

The VM started up, but no GUI came up, instead, a black screen with a terminal (I think it's called a Virtual Terminal) came up and asked me to log in. I tried the command "startx" from there, and it told me no screens were found.

What can I try?

---

### Post by sdowney717 on 2010-10-14
[http://ubuntuforums.org/showthread.php?t=1587206&page=2](http://ubuntuforums.org/showthread.php?t=1587206&page=2)
try following this. I always use the binary from nvidia.

right now running this one
[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)

I install from recovery mode.

---

### Post by l4nd0fc0nfu510n on 2010-10-14
I'm not sure what I was supposed to try on that page, but I tried the instructions that were furthest down the page, still doesn't work.

---

