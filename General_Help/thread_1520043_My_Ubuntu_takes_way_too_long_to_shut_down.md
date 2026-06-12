---
title: "My Ubuntu takes way too long to shut down"
date: 2010-06-29
forum: General Help
---

### Post by Evanescence on 2010-06-29
Hi,
am Maina and I have been using Ubuntu for like 1 year now and there's an issue I have never been able to understand. Am running Lucid (Gnome) and also Windows 7. My laptop has 2GB R.A.M, Intel Core 2 Duo. My problem with my Ubuntu is that it takes way too darn long to shut. It can take up to 2 minutes just to shut down, yet my Windows 7 takes less than 10 seconds. Is this normal for Ubuntu? is there something I can do to speed up shut down? start-up is OK though; its fast, but shut down is just annoyingly long.
Any advice is welcome and appreciated.

---

### Post by dino99 on 2010-06-29
you might search for usefull errors logged into .xsession-errors and into: system admin logviewer

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

will force a fsck on next reboot:
sudo shutdown -r now

are you using only genuine ubuntu repo and main server ?

---

### Post by coldraven on 2010-06-29
I have a similar set-up, my laptop will shut down in about 10 seconds.
You must have some process running but I not a Linux expert (yet!)
Some kind soul on this forum will sort it out, hopefully!

---

### Post by Evanescence on 2010-06-29
> **dino99 said:**
> you might search for usefull errors logged into .xsession-errors and into: system admin logviewer

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

will force a fsck on next reboot:
sudo shutdown -r now

are you using only genuine ubuntu repo and main server ?
OK. Thanks a lot

---

### Post by Evanescence on 2010-06-29
> **Evanescence said:**
> OK. Thanks a lot
Thanks. 
Yes am using a genuine repo and the main server. How do repos affect the speed or working of my Ubuntu?

---

### Post by dino99 on 2010-06-29
some users sometimes used personal packages and/or custum settings, then forget them for a while, and did not realised that their issues come from there, so its important to use genuine packages and trusted repo

---

### Post by philinux on 2010-06-29
Evanescence,

You need to look at this file.

/var/log/syslog either with nautilus or from System>admin>Log file Viewer.

Have a look though this file and try to locate where the machine is shutting down. 

Use View>Find and use killed as the search term. See if any messages are there. You can see below my normal shutdown messages from syslog. It takes about 4 seconds for my machines to shutdown.

```
Jun 29 11:50:41 desktop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Jun 29 11:50:41 desktop init: tty4 main process (941) killed by TERM signal
Jun 29 11:50:41 desktop init: tty5 main process (945) killed by TERM signal
Jun 29 11:50:41 desktop init: tty2 main process (953) killed by TERM signal
Jun 29 11:50:41 desktop init: tty3 main process (955) killed by TERM signal
Jun 29 11:50:41 desktop init: tty6 main process (957) killed by TERM signal
Jun 29 11:50:41 desktop init: cron main process (982) killed by TERM signal
Jun 29 11:50:41 desktop init: tty1 main process (1217) killed by TERM signal
Jun 29 11:50:41 desktop kernel: Kernel logging (proc) stopped.
```

---

### Post by Evanescence on 2010-06-30
Hi, am experiencing difficulty with System>Admin>Log File Viewer>View>Find... 'cause when I search with term "killed" as you told me, nothing seems to be happening. I was rather expecting a result pretty much like the one you got, but am not. 
am I supposed to select something on the left side of the window before I search?

---

### Post by Jakiejake on 2010-06-30
> **Evanescence said:**
> Hi,
am Maina and I have been using Ubuntu for like 1 year now and there's an issue I have never been able to understand. Am running Lucid (Gnome) and also Windows 7. My laptop has 2GB R.A.M, Intel Core 2 Duo. My problem with my Ubuntu is that it takes way too darn long to shut. It can take up to 2 minutes just to shut down, yet my Windows 7 takes less than 10 seconds. Is this normal for Ubuntu? is there something I can do to speed up shut down? start-up is OK though; its fast, but shut down is just annoyingly long.
Any advice is welcome and appreciated.

My computer is gone gone in 5 seconds or so with Ubuntu
Windows was like 10 or 15!

---

### Post by gbi on 2011-03-30
I am also using ubuntu 10.10 and every time update it. but it takes more than one minute to shut down. 
I am using compaq 510 with 2gb ram and core 2 duo 2.4 processor.
please help me if some one knows to fix this problem.

---

