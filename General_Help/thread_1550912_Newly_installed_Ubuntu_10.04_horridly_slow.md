---
title: "Newly installed Ubuntu 10.04 horridly slow"
date: 2010-08-11
forum: General Help
---

### Post by jimson69 on 2010-08-11
I'm new to Ubuntu, but not new to Linux/Unix.  I've just installed Ubuntu 10.04 on an older Toshiba Tecra M5 system w/4GB of memory and plenty of disk space.  What's weird is that I've hit this problem twice, now, where I'll the system for a day or so and then it creeps to a near halt.  I've reinstalled once, after first hitting the problem in the exact same manner...used for a day with no problems and then a complete slowdown.  The laptop 

When the problem happens, EVERYTHING is slow...launching apps, switching focus to a background apps (via mouse or alt-tab), browsing with firefox, thunderbird email.

When the problem is happening, it seems that firefox and Xorg are using quite a bit more CPU resources than when it isn't happening.  The weird thing is I'm not doing anything intensive with firefox, etc.  I did manually install the Nvidia video drivers and that didn't help.

I want to give Ubuntu a chance, but if I can't fix this, I'm running to try Suse or Mint OS.  

Thanks,
Jim

---

### Post by elricscripts on 2010-08-12
I hope someone can help with the speed factor you're experiencing.  I just wanted to say, you may be happier installing something like Ubuntu 8.04 on your slower system.  I see that the Toshiba Tecra M5 is aimed at Windows XP or around that range of operating system.

Maybe there are Ubuntu setups or versions that suite your system well.  Good luck.

---

### Post by lovinglinux on 2010-08-12
Open the System Monitor and check if some application is using too much RAM. If you have a memory leak in Firefox, for example caused by some extension, it could behave like that.

High CPU usage could be caused by Flash, bad javascript on a web page or even some extensions functions. 

Check my [Firefox tutorials]("http://firefox-tutorials.blogspot.com") for troubleshooting and optimization.

---

### Post by Ezunsecuredloan on 2010-08-12
I've been using Ubuntu 10.04 Lucid Lynx for a week now and I appreciate the change in looks of the desktop..

---

### Post by jimson69 on 2010-08-12
Yeah, forgot to post that this really isn't a memory problem, as top shows plenty of memory free...2.9 GB or so.  I don't think this is a flash problem, either, cause I'm using the same sites when it is fast or slow.  

When the problem happens, it seems 'firefox' and xorg take about 50 - 100% of the CPU cycles from the box.  I am using the firefox for the same functions on OpenSolaris and not only do firefox/xorg not run as hot, but the kernel scheduler seems to deal better with any cpu spikes (without affecting the user).

I really like the Ubuntu desktop, but can't live the performance.

---

### Post by tommah04 on 2010-08-13
hello,

you might wanna make sure you have activated your Video Card... it always seems to run slower before installing it for some reason.  just go to System>Administrator>Hardware Drivers... I did that, restarted and the computer was nice and quick.

if you've already done that... I'm out of ideas so good luck!

---

