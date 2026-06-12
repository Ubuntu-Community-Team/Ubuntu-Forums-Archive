---
title: "Multiple computers all have different problems with 10.10"
date: 2011-01-30
forum: General Help
---

### Post by butch1 on 2011-01-30
1. Desktop. Cannot play games on pogo.com. The applet either does not load correctly or it does not load. System works fine under virtualbox using XP. Have followed all instructions on website to solve problem including clearing cache and downloading new versions of java. Previous version of Ubuntu worked fine.
2. Laptop Acer, looses internet connection consistently both wireless and wired connection. Have removed power saving features and still cannot maintain connection to wired network. Previous Ubuntu installation worked fine.
3. Upgraded neighbor to Ubuntu 10.10 after windows virus attack. Have major problems with GEforce 6100. flickering, Typically after opening firefox and moving to several web pages. It does not happen right away but only after several web pages have been opened and then you can close the pages and flickering continues at fairly rapid rate. Have tried different drivers from NVIDIA with no effect.

It seems 10.10 was not ready for release and has major bugs that SHOULD have been addressed prior to making it available. Slavish adherence to a release schedule regardless of whether or not the software is stable is a contributing factor I believe.

---

### Post by e-San on 2011-01-30
Since i killed my os for a while i can not call packages you can try to install, but, try to find jre from sun for example and try chromium or opera.
 
it is answer for 1, ofcourse.
 
2. try to find package network-manager with dbg
run 'gdb nm-applet' after killing nm-applet, and wait for disconnection, tell what we have
or try to find some usefull information in dmesg.
 
3. try to blacklist kenrel's nVidia drivers.
 
please, provide wich sort of software you use.
 
i agree with you. in my opinion 10.10 is not worked well.
if you lost your patients, install 10.04.

---

### Post by butch1 on 2011-01-30
1. The Pogo problem exists under Epiphany also. I have downloaded new Java from Sun and loaded it but still not working.  My wife uses this computer and she can log into vitualbox and run XP to get the site to work properly. But it is a disaster for the reputation of UBUNTU to have to do that. I also had to disable the screen saver/power save/ applications to maintain an internet connection. What a waste! 

2.As far as my Neighbor is concerned I will probably try to revert to an earlier version, before wiping the disk and reinstalling windows as the only operating system.

3, The laptop I will wipe and install another distro. It took quite a while to get the system working previously, and now that i am having major problems I will just abandon Ubuntu for this system. I simply do not have the time to do the work which Canonical should have done before making the release available. What a disaster!

---

