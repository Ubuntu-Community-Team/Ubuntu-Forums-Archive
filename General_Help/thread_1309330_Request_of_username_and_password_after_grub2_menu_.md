---
title: "Request of username and password after grub2 menu on tty1"
date: 2009-11-01
forum: General Help
---

### Post by kickapu on 2009-11-01
Hi all, i'm having theis strange problems with karmic koala 64 bit... When i Boot, i choose the O.S. (i have 3 Vista 32 Bit, Jaunty 64 bit,Koala 64 bit), then the new ubuntu logo in white appears... then after 5 sec all screen goes black and the systems request me username and password with these line:

Ubuntu 9.10 PC tty1
PC login:
password:

where PC is the name I choose for my machine.

If i put it, the boot will go on normally, if i don't, the system waits about 30 sec then boot up normally.

I don't know what it cause this... i don't know where to start to solve this wasted of time at each booting up...

Somebody could give me a clue?

---

### Post by calanor on 2009-11-01
try this
go to system->administration->login screen unlock it and choose login as automatically and uncheck allow sec for someone else to login.

---

### Post by kickapu on 2009-11-01
Problem Solved.

It was a Nvidia Driver problem.

This Link for more details: [http://www.uluga.ubuntuforums.org/showthread.php?t=1305459&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1305459&page=2)

Howewer i did a little bit different (and easier).

I went to System-Administration-DriverHardware

I choose to remove the Nvidia Driver previously installed (185), Then i clean up my system for all the waste that this installion did (i used Bleachbit + Ubuntu tweak for the Cleaning, both downlodable from Ubuntu Software Center, under Application menu). I rebooted, then i Installed the 185 Nvidia driver again. Rebooted. Then all goes smooth as intended. I did such 10 reboot since i fixed the problem and still go smooth.

I Hope this thread can help people that will be in my same condition.

---

